---
title: "Lyx, installing customized class"
date: 2009-08-30
forum: Education &amp; Science
---

### Post by wenhaosparty on 2009-08-30
I just cannot get it work. Here is my conditions:

Lyx version 1.6.2;
Ubuntu 9.04

Goal: Writing thesis with it.

I found a good *.sty file here:
[http://help-csli.stanford.edu/tex/suthesis/](http://help-csli.stanford.edu/tex/suthesis/)
and I want to use this sty file in Lyx.
what I can get from this site include:
1. setspace.sty
2. suthesis-2e.sty
3. suthesis-abstract.sty

=============================================
What I have tried
=============================================

1. Installed *.sty by copying the files into "\usr\share\texmf/tex/latex" folder, then "sudo texhash"
2. I read Chapter 5 in the customization manual of Lyx. I know I need to write a layout file for it to work, and here is where the problem comes.

Here is my code

> #% Do not delete the line below; configure depends on this
#  \DeclareLaTeXClass[report,suthesis-abstract.sty]{report (thesis_Stanford)}

Input report.layout

Style Title
    LatexName    title
End

Style Author
    LatexName    author
    LatexType    Command
End

Style Dept
    LabelString    "Dept"
    LatexName    dept
    LatexType    Command
End

My problem is:
1. How to use more than one *.sty file in the layout file? (All examples in the manual has only one *sty used)
2. How to use the predefined environment, such as "\author", "\dept" in the layout file, so that it is available in Lyx?

---

### Post by dirac14 on 2009-08-30
I 'm dealing with the same issue (with a different package ofcourse) !
Please somebody help!!!

---

### Post by Mr. Picklesworth on 2009-09-01
Well, at least they're good for something: bumping threads that need answers. Thanks, Nike spam bot!

Edit: Don't mind me. I was talking to a ghost.

---

### Post by GSBoomer on 2009-09-01
A bunch of years ago I wrote my dissertation with LyX at Florida State using a latex class someone in the mathematics department had written. I found my fsuthesis.layout file:

```
#% Do not delete the line below; configure depends on this
#  \DeclareLaTeXClass{fsuthesis}
# FSU Thesis definition file.

# Input general definitions
Input stdclass.inc

# a few changes to the section
Style Section
  Align                 center
End

# a few changes to the section*
Style Section*
  Align                 center
End

```

All this does, of course, is change the way the Section and Section* layout appears on the screen in LyX. It really has no effect on the final file.

For many of the environments, I simply inserted LaTeX code (evil red text). IIRC, I some of the values I simply defined in the preamble and they 'magically' appeared in the appropriate places. 

I will say that Mimi (the woman who wrote the latex class) was very helpful and even re-wrote some of the class file to work more easily with LyX. For some issues, you may need the original author's help.

---

