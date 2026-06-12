---
title: "Randtext package for texlive not working"
date: 2010-05-22
forum: Education &amp; Science
---

### Post by Morrad on 2010-05-22
I apologize if this is in the wrong forum, but to me this seems like the place to go for people who know how to use Latex.

I'm trying to write my resume in Latex, and am wanting to obfuscate some things such as my email address and phone number.  The randtext package of texlive-latex-extra provides a \randomize{TEXT} function which is supposed to perform this functionality.

When copying text from a sample file (tex source included below) in evince, however, the text does not end up obfuscated.  What am I doing wrong?  Does evince use some alternate means of copying so that it doesn't appear to work?

Relevant README files and such included below.  I have also verified that the random.tex referenced in randtex.sty is included.

```
$ cat /usr/share/doc/texlive-doc/latex/randtext/README
The package "randtext.sty", which supersedes "switcheml.sty", provides a 
single macro \randomize{TEXT} that typesets the characters of TEXT in 
random order, such that the resulting output appears correct, but most 
automated attempts to read the file will misunderstand it.

This function allows one to include an email address on a TeX document 
and publish it online without fear of email address harvesters or 
spammers easily picking up the address.

For more information, please read the comments at the top of the package 
file.
```

```
$ head -n 38 /usr/share/texmf-texlive/tex/latex/randtext/randtext.sty
%
% randtext.sty
%
% Charles Duan (2004/12/20)
%
% Provides one useful macro, \randomize{TEXT}. Result is a typeset box that
% looks, on paper, like TEXT, but whose letters have in fact been placed in
% random order so that they are not copiable from the file directly.
%
% In other words, typing:
%
%   This is a \randomize{random-text} test.
%
% would produce output that looks like:
%
%   This is a random-text test.
%
% but if you tried to copy-paste it from the output file, you would probably get
%
%   This is a mdoxt-etnra test.
%
% The function of this odd macro is to obfuscate e-mail addresses, say on a PDF
% document put online, so that the human reader sees the address as expected,
% but e-mail address harvesters and spambots cannot determine the address. Since
% this macro is done entirely using TeX typesetting commands, it requires no
% external image generation or anything, and the typeset result is just as
% high-quality as if no obfuscation had taken place.
%
% This macro does take into account kerning between character pairs, but it does
% not account for ligatures. To make appropriate ligatures, surround the
% ligature characters with braces.
%
% This package supersedes "switcheml.sty", written by the same author. (That is
% the reason that the internal macros begin with "se@".
%
% Requires the file "random.tex", by Donald Arseneau. I believe that this file
% comes as part of a standard TeX distribution.
%
```

```
$ cat test.tex
\documentclass[12pt]{article}
%
% Add the randtext package
\usepackage{randtext}
\title{Test}
\date{}
\begin{document}
\maketitle 
randomize{abcdefg123456789}
\end{document}
```

---

### Post by FreeTheBee on 2010-05-22
Hi, I ran a quick test and for me it is the same. If I make a pdf I can copy the text both with evince and okular. It does work when I make a dvi though.

---

### Post by Morrad on 2010-05-22
I hadn't tried making any other output formats.

What are you using to look at the dvi file?

When I create a dvi file from the sample (using the pslatex command), I can't select any of the text at all when opening the dvi file in evince.  If I convert the resulting dvi file to a pdf (using dvipdf command), the text is copyable without obfuscation as before.

---

### Post by FreeTheBee on 2010-05-22
I made the dvi just using latex instead of pdflatex and opened it in okular. Evince gave an error. The problem with pdf is mentioned here as well,

[http://magic.aladdin.cs.cmu.edu/2007/12/09/protect-your-email-address-in-ps-and-pdf/]("http://magic.aladdin.cs.cmu.edu/2007/12/09/protect-your-email-address-in-ps-and-pdf/")

It seems it might work in some cases, but is by no means full proof.

---

### Post by Morrad on 2010-05-22
Ah, I see.  So it sounds like for evince (and presumably other pdf display software) the obfuscation doesn't work since they just "read" the pdf as we would to determine the selected text.

Thanks for pointing out that explanation.  I think I had found it earlier today searching on my own, but the explanation hadn't clicked until I revisited it.

---

