# Introduction: A&A-bibstyle-with-hyperlink
- modified `aa.bst` with clickable url links in the bibliography
- bst file for Astronomy & Astrophysical Journal
- modified based on the `aa.bst` file from http://ftp.edpsciences.org/pub/aa/readme.html
- it is recommended to **use the bibtex record generated from NASA/ADS** in order to include `doi` and `adsurl` properly

# How to use:
- Put this `aa_url.bst` in your project folder and reference this with `\bibliographystyle{folder/aa_url.bst}`
- For making the links and colors work, **MAKE SURE** to add something like the following in the preamble of your .TeX file

```
%---------- Add the clickable link function ----------
\usepackage{color}
\usepackage{natbib,twoopt}
\usepackage[hyphenbreaks]{breakurl}
\usepackage[breaklinks]{hyperref}      %% to avoid \citeads line fills, add "draft" 
                                       %% to avoid the PDFTK error (broken links)
\bibpunct{(}{)}{;}{a}{}{,}             %% natbib format for A&A and ApJ
\definecolor{cobalt}{rgb}{0.06, 0.2, 0.65}
\hypersetup{
  colorlinks,
  citecolor=cobalt,
  linkcolor=[rgb]{0.8, 0.2, 1.0},
  urlcolor=cobalt,
}
\makeatletter
  \newcommandtwoopt{\citeads}[3][][]{\href{http://ui.adsabs.harvard.edu/abs/#3}%
    {\def\hyper@linkstart##1##2{}%
     \let\hyper@linkend\@empty\citealp[#1][#2]{#3}}}
  \newcommandtwoopt{\citepads}[3][][]{\href{http://ui.adsabs.harvard.edu/abs/#3}%
    {\def\hyper@linkstart##1##2{}%
     \let\hyper@linkend\@empty\citep[#1][#2]{#3}}}
  \newcommandtwoopt{\citetads}[3][][]{\href{http://ui.adsabs.harvard.edu/abs/#3}%
    {\def\hyper@linkstart##1##2{}%
     \let\hyper@linkend\@empty\citet[#1][#2]{#3}}}
  \newcommandtwoopt{\citeyearads}[3][][]%
    {\href{http://adsabs.harvard.edu/abs/#3}
    {\def\hyper@linkstart##1##2{}%
     \let\hyper@linkend\@empty\citeyear[#1][#2]{#3}}}
\makeatother
```

# Examples:
This is a demo of the function of this bibstyle.

![example](./example.png)


## Notes:
- Some users report that the `color` package generates some warning and switch to `xcolor` might help.
