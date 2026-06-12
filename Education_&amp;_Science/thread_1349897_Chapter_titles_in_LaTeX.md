---
title: "Chapter titles in LaTeX"
date: 2009-12-08
forum: Education &amp; Science
---

### Post by kbaumen on 2009-12-08
When

```
\chapter{name}
```is typed in a .tex file, it usually starts a new page and makes a title in two lines. The first line, has **Chapter n** and the second line has the name of the chapter (in this case **name**). Is it possible to change the way this command operates? For example, I'd like to have a new page, where the title consisted of just one line - **n name**? What I mean is, is it possible to get the \chapter command to operate as a \section command but also start a new line. Just reducing all chapters to sections, all sections to subsections etc doesn't work, because my document contains subsections which if reduced to paragraphs are not numbered anymore and do not appear in the table of contents. 

Cheers for any help.

EDIT:
Nevermind, I solved the problem. Just had to add
```
\renewcommand{\chaptername}{}
```
in the preamble.

---

