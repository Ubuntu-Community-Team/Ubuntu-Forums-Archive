---
title: "cannot open Large documents"
date: 2008-06-13
forum: Desktop Environments
---

### Post by a1z on 2008-06-13
I edit large documents (doc, txt, rtf). I cannot open some of these documents longer than 100 pages. The window halts and stays as blank.

My CPU is 2 DUO 2GB. Ram=4GB. Windows XP can open after some delay. MS Word can handle 30K+ pages of Word document. XP can handle 150MB plain text documents. But Ubuntu can't.

I made 4GB swap space, use Gnome without desktop effect. I still cannot open even plain text - but large - documents as I could in XP.

Any advice is appreciated.

---

### Post by zaivala on 2008-06-14
OpenOffice's ability to open large documents is regulated by the amount of RAM you have, in my experience.  I had a similar complaint when I had 512 Mb of RAM, but it went away when I upgraded to 1 Gb.  (I now have 2.5 Gb)

There are other problems with OpenOffice, but they may not affect your use.  I have a couple of topics open at the OOo forum.

Also, have you tried AbiWord (or, if you use KDE, KEdit)?  I have found that most of the problems I have with OOo are either missing or much less in AbiWord.

Moss

---

### Post by a1z on 2008-06-14
Moss & other readers:

Thanks for a quick reply. I have tried the following:

1.	I downloaded and used OoWriter, Abi, KWord, gEdit, and any available word processor found in Synaptic installer database. I opened the plain text document. Frozen & Negative
2.	I modified OoWriter to disable Java, changed how many steps to store Undo events, reallocated how much memory for each Undo step. Still Negative.
3.	One time I installed Word 2003. It opened the document until the last page. But upon closing it the software, not the document, crashed.
4.	I fresh-installed Kubuntu, KDE, KEdit. Negative. OS&SW cannot open it.
5.	I fresh-installed Ubuntu, Gnome, deleted all compiz, and any graphic enhancement component. Still Negative.
6.	Observation1: When I open a 150MB plain text document, WinXP does use much of CPU plus some PF (page file?) memory. I expected Ubuntu to use some swap memory. I have not seen my swap graph-line fluctuate.
7.	Observation2: 2GB Duo & 4GB. If this is not enough, maybe my demand surpasses the capacity of my hardware. If this is the case, I shall remain until a 8GB unit is ready.
8.	Question: Is there a way to force – or redirect – Ubuntu to use swap first before using the main 4GB RAM? (Or is this a disadvantage because swap usage drags the speed of the HDD reading?) Can, or should, the memories (both RAM and swap) be used together under heavy workload? In my observation, XP uses RAM first and if needed use PF memory.

Again, thanks and I appreciate your time and comment.

A1Z

---

### Post by zaivala on 2008-06-14
I'm not sure what your problem is.  As a professional editor, I have opened 250+ page books (as .doc) without a problem (when I only had 1 Gb of RAM) -- at least with the loading.  My problem has been that I get everything edited, save it, looks good... then as soon as I re-open the file, I find some paragraphs formatted differently (vertically and horizontally) and with different font faces and sizes... and when someone else opens the file in Word, some of those font faces come out as Small Caps.  This has been validated by other users; in theory, I should be able to use Styles in some way as to fix this issue, but that, too, would make something look wrong when reopened in Word.

At this point, OpenOffice.org is the most developed Linux office package... which is a bad thing, in my opinion, because if they ever get it to where it works in all the ways I need it to work, I can leave Windoze forever.

Moss

---

### Post by Enverex on 2008-06-14
I'm not sure what you mean by a Core2Duo 2GB unless you mean **2Ghz** (Bytes is a measure of size, Hertz are a measure of speed).

Really your system shouldn't be locking up or unable to open these files. I open 50+ MB files in Abiword and Bluefish and they only take a few seconds to open.

Checking what your system is going would be useful, no point making a SWAP or waiting for more RAM unless that's actually what the problem is.

---

### Post by twright on 2008-06-14
for the plain text document i recommend emacs, vi, nano or some other terminal based text editor

the new beta of open office might be faster

i think that somewhere you can set swappiness which controls how much you swap

---

