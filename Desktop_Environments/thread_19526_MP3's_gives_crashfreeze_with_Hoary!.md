---
title: "MP3's gives crash/freeze with Hoary!"
date: 2005-03-12
forum: Desktop Environments
---

### Post by Tubbie on 2005-03-12
The problem is that I can't play MP3 files.
And i've I wanna play one, the program crashes/freezes.

I've installed XMMS with these commands:

$ sudo apt-get install libmikmod2
$ sudo apt-get install xmms

But everytime I wanna start a mp3 it freezes XMMS.
I've also tried other players, but they won't play anything also.

I've reinstalled Hoary already, without any solution.
With the Warty release everything worked without a problem.

I'm using a Creative Soundblaster 128.
Anyone has a solution?

---

### Post by Tubuntu on 2005-03-13
Same problem here with hoary array6, amd64
xmms and Beep Media player freeze when trying to play mp3

Anybody? Solution? 

Just Upgraded from warty and I have used 30 hours to get it working, No sleeping, yes Ubuntu is the Best   :p

---

### Post by Tubuntu on 2005-03-14
Solved IT!!  :-D  


System->Preference->Multimedia System Selector-><Audio Tab> Choose Output "ESD -Enlightment...." 

XMMS <Hit Ctrl+p>  -> Audio Plugin Tab-> Output Plugin Choose "eSound Output..." 
Hit Ok and Play MP3s

and same work with beep media player...

It was really easy to solve. (it took only 35hours, I was just going to throw computer from the window and buying Playstation 2..)

---

### Post by espee on 2005-03-14
wooha! this is what I did all the time: applications -> system tools -> system monitor
In there I looked for 'esd' and I killed that process. Voila: xmms works

But I must say that your solution is way better ;o)

---

### Post by kb00heda on 2005-03-21
Tubuntu --- you rock!  :-D

---

### Post by Tubuntu on 2005-03-22
[QUOTE=kb00heda]Tubuntu --- you rock!  :-D[/QUOTE]


 :razz:  Yippeee!! 
Its nice to make somebody happy, thanks kb00heda 
 O:)

---

### Post by gregorian21 on 2005-03-25
Thanks Tubuntu,
You've definitely saved me a lot of time.

---

### Post by Tubuntu on 2005-03-25
[QUOTE=gregorian21]Thanks Tubuntu,
You've definitely saved me a lot of time.[/QUOTE]

Thanks!

---

