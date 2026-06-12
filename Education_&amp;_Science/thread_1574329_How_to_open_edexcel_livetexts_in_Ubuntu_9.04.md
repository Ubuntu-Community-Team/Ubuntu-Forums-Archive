---
title: "How to open edexcel livetexts in Ubuntu 9.04??"
date: 2010-09-14
forum: Education &amp; Science
---

### Post by tantrik369 on 2010-09-14
Hi friends, 
 
I am having a problem here. I have some **livetexts/activebooks** from **edexcel A-Level subjects** (C1, C2, C3 etc) which I can open and view in windows xp using **Mathplayer** and **internet explorer 7**. How can I open these livetexts in ubuntu along with the **solutionbank **(each  exercises in these livetexts comes with a solutionbank) ? Did anybody  try viewing and using livetexts in Mandriva or any other linux distro???  I don't have clue. 
 
Each livetext folder has **.swf, .jpg , .xml, .xhtml and .html** files. The solutionbank cannot be used in opera or firefox in windows xp. 
 
Please help me in this problem. 
 
Thanks in advance.

---

### Post by scottuss on 2010-09-14
Looks like the stuff is accessible from a web browser, maybe look for an index.html file or similar and open that in Firefox.

---

### Post by josepaul on 2010-10-05
hi, bit of a late reply, but I was in the same position not too long ago. Livetext is pretty much a no as it is not a widely used program, but for the solutionbank, what I did was, used the WINE to emulate internet explorer

I am pretty sure I used this;

[link]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

EDIT: this should help too; [link]("http://webexpose.org/2007/01/07/internet-explorer-7-on-linux/").

---

### Post by josepaul on 2010-10-05
> **scottuss said:**
> Looks like the stuff is accessible from a web browser, maybe look for an index.html file or similar and open that in Firefox.

it doesnt work in anything other than the internet explorer as active x is needed

---

### Post by nicku on 2010-10-08
hia, I've been looking at this problem too

I'm working with 10.04 and the S1 cd, but i imagine the ideas apply to the other modules. The flash version of the livetext   -  named LiveTextViewer.swf;1 works fine in the windows version of firefox.  It seemed to me that the problem may have been caused by filename conventions. A large number of the filenames on the cd have the suffix **;1**  (no idea why) - If you remove these then the livetext works under ubuntu firefox.

I did this by using the command **rename 's/\;1$//' *\;1**  in all the directories on the cd, though I imagine this could be automated.

Everything seems to work fine except for the solution bank answers. - This i think corresponds to a capitalisation in the filename of the files containing the answers

e.g. it tries to open **content/sb/content/s1_7_D_4.xhtml** instead of **content/sb/content/s1_7_d_4.xhtml**

if anyone can think of an easy way to automate this name change then t'would be appreciated

hope this helps...

---

### Post by nicku on 2010-10-08
the deal with the solutions seems to be as follows

the livetext does not have the capitalisation error. the solution bank does.

the live text gives links to the solution for one question in each set. Since the solution bank has the capitalisation error, one may then not retrieve the other solutions. One may enable the solution bank to access the other solutions via running the script

[B]#!/bin/bash

for file in *
do
newfile=`echo $file| sed 's/_a_/_A_/g'`
newfile=`echo $newfile| sed 's/_b_/_B_/g'`
newfile=`echo $newfile| sed 's/_c_/_C_/g'`
newfile=`echo $newfile| sed 's/_d_/_D_/g'`
newfile=`echo $newfile| sed 's/_e_/_E_/g'`
newfile=`echo $newfile| sed 's/_f_/_F_/g'`
newfile=`echo $newfile| sed 's/_g_/_G_/g'`
mv $file  $newfile
echo $file  moved to $newfile
done[/B]

in the folder **content/sb/content **on the cd, however this then breaks the link from the livetext to the solution bank. Although this allows an 'already open' solution banks to access all solutions, it is a horrendous workaround as all filenames would have to be reverted back to their original forms next time one wants to open the solution bank.

ugh....

any ideas on how to get both working at the same time?

---

### Post by nicku on 2010-10-09
....quick way to remedy this is to change the mv command in my previous post to a cp. Then both capitalised and non-capitalised forms of the files exist, and both livetext and solutionbank are happy...

---

### Post by josepaul on 2011-01-08
> **nicku said:**
> ....quick way to remedy this is to change the mv command in my previous post to a cp. Then both capitalised and non-capitalised forms of the files exist, and both livetext and solutionbank are happy...

so you got livetext working under ubuntu? 

btw are you an a level student

---

### Post by tantrik369 on 2011-03-10
> **nicku said:**
> ....quick way to remedy this is to change the mv command in my previous post to a cp. Then both capitalised and non-capitalised forms of the files exist, and both livetext and solutionbank are happy...

Thanks for the help. But now I am having another trouble. With the solution you gave, I could open edexcel livetext C1 with its solutionbank at ease in firefox, but cannot open solutionbank of FP3 (I could open livetext though). When I try to open FP3 solutionbank on ubuntu in firefox, I see blank pages with headings, "question" ,"solution". I tried these at some other linux distros the result being the same. 

I placed libflashplayer.so in plugins folder of firefox but to no avail. May be Mathplayer is needed, since on win xp, mathplayer is used for internet explorer to show the workings of the solutionbank.

Kindly please help how do I overcome these problems.

Thanks in advance.

---

