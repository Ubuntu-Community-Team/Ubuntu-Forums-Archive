---
title: "Help with importing JabRef references to LyX"
date: 2010-02-18
forum: Education &amp; Science
---

### Post by r.mac on 2010-02-18
Hi, I have found a few threads relating to JabRef and LyX but none of them seem to deal with my problem. I am writing a paper in Springer LNCS format and have downloaded JabRef to handle the bibliography. I have inserted the bibliography file but when I try to view the LyX file as a pdf to make sure it worked properly I get a number of error messages relating to the bibliography.

   [FONT=Courier New]\cite{640634,1541999}}[/FONT]
 
 [FONT=Courier New]I've run across a `}' that doesn't seem to match anything.[/FONT]
 [FONT=Courier New]For example, `\def\a#1{...}' and `\a}' would produce[/FONT]
 [FONT=Courier New]this error. If you simply proceed now, the `\par' that[/FONT]
 [FONT=Courier New]I've just inserted will cause me to report a runaway[/FONT]
 [FONT=Courier New]argument that might be the root of the problem. But if[/FONT]
 [FONT=Courier New]your `}' was spurious, just type `2' and it will go away.[/FONT]
[FONT=Courier New]
[/FONT]
    [FONT=Courier New]\cite{640634,1541999}}[/FONT]
 
 [FONT=Courier New]I suspect you've forgotten a `}', causing me to apply this[/FONT]
 [FONT=Courier New]control sequence to too much text. How can we recover?[/FONT]
 [FONT=Courier New]My plan is to forget the whole thing and hope for the best.[/FONT]

[FONT=Courier New] \cite{640634,1541999}}[/FONT]
 
 [FONT=Courier New]I'm ignoring this; it doesn't match any \if.[/FONT]


[FONT=Arial][FONT=Trebuchet MS]Leaving aside the rather HAL like commentary, it seems that the problem is that JabRef is writing the references in a way that LyX doesn't like. Does anyone have any experience with this problem?[/FONT][/FONT]


[FONT=Arial]Hope you can help, the deadline for articles is tomorrow!
[/FONT]

---

### Post by r.mac on 2010-02-18
apologies, it seems this was some kind of odd bug. I imported the database again, and this time it works fine. If a moderator wants to delete this thread, then please do.

---

