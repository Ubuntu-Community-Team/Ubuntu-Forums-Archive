---
title: "EPS file not opening"
date: 2007-10-24
forum: Education &amp; Science
---

### Post by one_ro on 2007-10-24
Dear all,

I have read all posts I found about LaTeX and EPS files, but nothing works so far. I'm using Kubuntu Feisty, and my problem relates to the impossibility of viewing the EPS graphics in the DVI file.

I use the graphicx package in the preamble (w/ or w/o [dvips] in front it makes no difference here).

I believe there's nothing wrong with the EPS files, as I get the same error whether I create them with Inkscape, Gimp, R or OpenOffice.

What can I do further to preview the graphics in KDVI? (evince or xdvi do not present the graphics either)

Even more, I cannot open any EPS file in Kubuntu. All software (KGhostView for example) report the very same problem:
```
CRIT: rangecheck in get
Operand stack:
          0

```When opening xvdi, I get this first on the console:
```
$ xdvi
gs: CRIT: rangecheck in get
gs: Operand stack:
gs:           0
xdvik: read_from_gs: Connection reset by peer

```Someone suggested to verify the output of the following command:
```
$ identify -list format
[...]
identify: unable to open module file
`/usr/lib/ImageMagick-6.2.4/modules-Q16/coders/magick.la': No such file or directory.
```

I'd be forever grateful to anyone for a hint,
Adrian

---

### Post by lordmyth on 2008-01-04
I'm having the same problem, except it appears when printing pdfs (postscript printer)
[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg155161.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg155161.html)
This is the bug from debian testing

---

### Post by one_ro on 2008-01-04
It looks like the problem is partially solved in Ubuntu Gutsy, as the EPS files now appear in the DVI file.
The other part of the problem I am now facing is related to transparency: in the PDF file they look perfect, but in the DVI file figures use only fundamental colors with no transparency.

Hopefully, the problem will eventually be solved in the next versions.
Thanks for replying,
Adrian

---

