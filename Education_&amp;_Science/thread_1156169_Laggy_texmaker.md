---
title: "Laggy texmaker"
date: 2009-05-11
forum: Education &amp; Science
---

### Post by BramWillemsen on 2009-05-11
Hello everyone,

I'm having some lag issues with texmaker. I've tried to google a bit but i didnt manage to find a solution. Whenever i type or move the cursor around with my keyboard i can feel a big delay, the cursor lags behind. This only happens in texmaker and only in documents that fill my entire screen. I got a pretty fast computer (amd x2 5600+ and 2 gig of memory) so i guess something is going wrong. When i open the same document in gedit (also with highlighting) everything is very smooth.

Did anyone experience something similar? 

kind regards, Bram

p.s. 

im using jaunty and texmaker 1.8

---

### Post by Red_Acid on 2009-05-11
Well, and that makes 2 of us.

Today, I had a lecture about LaTeX, so I've searched Ubuntu Forums, and the results pointed me Texmaker as the best TeX editor for Gnome (and 2 friends of mine, who already use Texmaker, said the same).

Aptitude did the installing job great as usual, and everything seemed nice until I've started to write. It is very laggy and the letters are buggy. I don't know what's up, 'cause in my friends case, Texmaker is very smooth.

Just like **BramWillemsen**, I have a nice machine too (Core2Duo 2.4GHz, 2GB RAM), and when I open the files in Gedit, everything is fine.


Best Regards.

---

### Post by BramWillemsen on 2009-05-12
on my laptop it works fine, its just my desktop computer that has laggy texmaker. Maybe this is related to the discontinued support for the ati x1950 video card? flgrx drivers don't work with it anymore. Do you have an ati card too? Just trying to find a connection between our cases, i'm not sure if it is the cause.

Bram

---

### Post by ad_267 on 2009-05-12
I haven't tried TeXMaker myself but there other alternatives. I quite like the LaTeX plugin for Gedit. Kile is also another good option.

---

### Post by BramWillemsen on 2009-05-12
yeah that is probably the next step that i'll take. Just wanted to find out if there was an easy fix for this :)

---

### Post by Red_Acid on 2009-05-12
> on my laptop it works fine, its just my desktop computer that has laggy texmaker. Maybe this is related to the discontinued support for the ati x1950 video card? flgrx drivers don't work with it anymore. Do you have an ati card too?
In my case, it's my laptop that has a laggy Texmaker. And my graphics card is a NVIDIA GeForce 9600M GT.

> I haven't tried TeXMaker myself but there other alternatives. I quite like the LaTeX plugin for Gedit. Kile is also another good option.
I already installed the LaTeX Plugin for Gedit, and it seems quite nice, but don't have all the options and easyness of Texmaker. And I don't like to much to use KDE libs, but maybe I'll have to go that way if there's not a fix for Texmaker.

---

### Post by kazza765 on 2009-05-13
> **Red_Acid said:**
> In my case, it's my laptop that has a laggy Texmaker. And my graphics card is a NVIDIA GeForce 9600M GT.


I already installed the LaTeX Plugin for Gedit, and it seems quite nice, but don't have all the options and easyness of Texmaker. And I don't like to much to use KDE libs, but maybe I'll have to go that way if there's not a fix for Texmaker.

Just thought I'd let you know, I'm having the same problem here with NVIDIA GeForce 9500GT. I guess I'll just move on to Gedit if there's no fix for this.

---

### Post by meborc on 2009-05-15
just to confirm, my friend who has a small laptop with intel integrated graphics has random texmaker slowdown... it takes few seconds for the typed text to appear in the window... other applications (including window effects) work just fine

btw, the slow down occurs both WITH and WITHOUT the window effects

---

### Post by Humphreybas on 2009-11-20
Finally fed up too much by laggy texmaker (modern laptop with intel graphics) I also decided to fix the problem. Google gave me this topic with no solution, and nothing else.
I decided to update to the latest version 1.9.2 (not in repositories, go to the texmaker site to download the .deb package). And now it runs smooth :) 

offtopic:
And on top of it there are more improvements which I like (only had it for 5 min.) but I like that the spelling check is now automatic with red lines under wrong words :)

---

### Post by jtchipman on 2009-12-17
I don't normally post, but I thought I should second the suggestion to update to the newest version of Texmaker (not currently in the repositories). It does not lag on my 1.6 CPU w/ newest Ubuntu.

---

