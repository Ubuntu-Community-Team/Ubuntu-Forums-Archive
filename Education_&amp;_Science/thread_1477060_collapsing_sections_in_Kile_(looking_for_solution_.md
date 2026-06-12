---
title: "collapsing sections in Kile (looking for solution or other program)"
date: 2010-05-08
forum: Education &amp; Science
---

### Post by P3t3r on 2010-05-08
I've been using Kile for a while, and overall I'm very satisfied, but I'm having one big problem with it.

If I'm writing a big document, with several chapters and sections, I want to be able to collapse several chapters and sections, so that I have a reasonable view on just the current section I'm working in.

Just using ```
\chapter A
  \section A.a
    text
  \section A.b
    text
\chapter B
    text
``` doesn't work (Kile shows no collapse butten), so I use the less standard syntax ```
\begin{chapter}{A}
  \begin{section}{A.a}
    text
  \end{section}
  \begin{section}{A.b}
    text
  \end{section}
\end{chapter}
\begin{chapter}{B}
    text
\end{chapter}
``` but somehow this seems buggy: sometimes it collapses too much, sometimes scrolling goes crazy (showing some lines twice, for exaple), etc.

So I assume I'm doing something wrong. What's the proper way to make chapters and sections collapsible in Kile, and if it's not possible, what other programs can do this (preferrably also having environment autocompletion and multiline indentation)?

---

### Post by P3t3r on 2010-05-17
I guess that's a no? Which programs do you use for writing larger documents in one file (like a MSc thesis)?

---

### Post by jetpeach on 2010-05-17
i'm not exactly sure what you mean by collapse to have a reasonable view- are you using the structure view in kile? it will show all the sections/chapters etc and is customizable as to what you want/don't want it to show, and any chapter or section can be minimized with the minus sign... clicking takes you wherever you want to go.

or is it in the structure view that you are referring to? my sections have always been collapsible, i make them using
\chapter{chapter name here}
\section{section name here}
\subsection{subsection name here}

hope this helps

---

### Post by P3t3r on 2010-05-20
Well it's very interesting to hear that this is actually possible in Kile. However I still fail to find how it works. Could you detail a bit more?

I have the "structure view", but I don't get how it can make sections collapse in the text window, in a similar way as Kile does collapse environments? Yes, you can jump to a section of your choice, but that doesn't collapse the other sections (in the text view)?

And when I write
\chapter{chapter name here}
\section{section name here}
\subsection{subsection name here}
then Kile does not see it as a collapsible environment. What am I doing wrong?

---

### Post by FreeTheBee on 2010-05-20
Hi, out of the box kile does not do this. But perhaps it is possible to fix it in the latex.xml file in the /usr/share/kde4/apps/katepart/syntax folder (on my system). I did a quick test, adding a beginblock to the sectioning item, and it did enable folding. Minor issue, it folded everything below the section I tried to fold. Perhaps with some fiddling it is possible to set it up properly. Make sure to back up the original before playing.

TexmakerX and vim-latex both support code folding out of the box, I have no experience with texmakerx though.

To make long documents more easy to navigate I usually make a master document with several input files. Setting up a project in Kile allows you to always compile the master, even when editing one of the sub documents. It would be nice to have proper folding as well though.

---

### Post by P3t3r on 2010-05-21
Well, the syntax I proposed
```
\begin{chapter}{A}
  \begin{section}{A.a}
    text
  \end{section}
  \begin{section}{A.b}
    text
  \end{section}
\end{chapter}
\begin{chapter}{B}
    text
\end{chapter}
```
allows folding, even without the minor bug you mention. Problem is, it is a bit buggy, and I suspect it is just buggy for all environments. So I wondered if there was a cleaner way. (Next to that it also breaks the structure view.)

For "normal" use you won't see the bug as you'll never fold such large blocks of text normally, but you clearly notice bugs when folding such large amounts of text.

---

### Post by excetara2 on 2010-10-21
I'm having the same problem. I can't collapse blocks of text and structure view is working. How do you hide the blocks?? does structure view have to be turned on since beginning. It works but not on chapters,sections, and subsections. It does work if I use deprecated format of \begin{subsection}{Title} \end{subsection}

Any help appreciated because it doesn't autocomplete the above but i will type like this if necessary.

Cheers,
Jeff

---

### Post by euclidean on 2011-09-15
I know this is an old thread, but I haven't noticed many other people mention this problem.

> **P3t3r said:**
> sometimes it collapses too much

Yes, this is my problem. It gets some of the begin/end tags right but many of end tags get missed so it often folds the entire rest of the document.

I tried it out in Kate as well and the same behaviour is there, so it seems to be an underlying issue with the editor part. However, most people using straight Kate will not be doing Latex so it probably goes unnoticed...

Not sure if anyone has more insight?

---

### Post by P3t3r on 2012-04-28
> **euclidean said:**
> I know this is an old thread, but I haven't noticed many other people mention this problem.



Yes, this is my problem. It gets some of the begin/end tags right but many of end tags get missed so it often folds the entire rest of the document.

I tried it out in Kate as well and the same behaviour is there, so it seems to be an underlying issue with the editor part. However, most people using straight Kate will not be doing Latex so it probably goes unnoticed...

Not sure if anyone has more insight?Bumping this again, is anyone aware of any progress being made on this? I know it's old as stone but it seems to be still as relevant as 2 years ago.

---

### Post by tdupu on 2012-05-03
The year is 2012 and the collapsing problem still exists. Wow.

---

