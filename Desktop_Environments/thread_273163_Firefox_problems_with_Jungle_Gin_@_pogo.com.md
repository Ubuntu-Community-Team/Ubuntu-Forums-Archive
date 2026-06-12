---
title: "Firefox problems with Jungle Gin @ pogo.com"
date: 2006-10-07
forum: Desktop Environments
---

### Post by StarsAndBars14 on 2006-10-07
Hey. . .I've already gotten JRE 1.50.06 from the Sun website and installed it, then followed their install instructions for Mozilla 7 (self-extracting .bin, 32 bit) and gotten Firefox to work with Java.  

However, when I go to Club Pogo ([http://pogo.com](http://pogo.com)) and try to play "Jungle Gin" the game refuses to load.  So I input ports 1024-65535 into Guarddog and set them to the IPs that were given by the Pogo support staff.  Now since the IPs they use change regularly this works fine. . .UNTIL I try to enter a room.  

The room options dialog box comes up, then after OK is clicked, the room comes up - and does one of two things:

1) Gets pogo.com to display an "Out of Memory - Unix" notice in the browser.  It says the game applet requires 3MB of memory in addition to what is already running.
2) Crashes Firefox completely.

I really hope there is a way to get this working, because my mom would like it and she's been waiting to unwind on a card game all day.  

Thanks for any help that can be given.

(EDIT:  I've reinstalled Java using the Ubuntu packages, and restarted the browser, but the java_vm application still takes up over 40 MB of resident memory and Pogo still displays the same notice.  

I don't remember memory management in Linux being this horrible.  Is this just an isolated incident?)

---

### Post by StarsAndBars14 on 2006-10-07
By the way! I am using 6.06 LTS.

Spades, Hearts and some of her other favorites work fine so I'm off the hook for a while. . .

It appears the only problems are being caused by Jungle Gin.

---

### Post by RJARRRPCGP on 2006-10-08
> **StarsAndBars14 said:**
> Hey. . .I've already gotten JRE 1.50.06 from the Sun website and installed it, then followed their install instructions for Mozilla 7 (self-extracting .bin, 32 bit) and gotten Firefox to work with Java.  

However, when I go to Club Pogo ([http://pogo.com](http://pogo.com)) and try to play "Jungle Gin" the game refuses to load.  So I input ports 1024-65535 into Guarddog and set them to the IPs that were given by the Pogo support staff.  Now since the IPs they use change regularly this works fine. . .UNTIL I try to enter a room.  

The room options dialog box comes up, then after OK is clicked, the room comes up - and does one of two things:

1) Gets pogo.com to display an "Out of Memory - Unix" notice in the browser.  It says the game applet requires 3MB of memory in addition to what is already running.
2) Crashes Firefox completely.

I really hope there is a way to get this working, because my mom would like it and she's been waiting to unwind on a card game all day.  

Thanks for any help that can be given.

(EDIT:  I've reinstalled Java using the Ubuntu packages, and restarted the browser, but the java_vm application still takes up over 40 MB of resident memory and Pogo still displays the same notice.  

I don't remember memory management in Linux being this horrible.  Is this just an isolated incident?)

I would be surprised if pogo.com games work with Firefox and Opera! 

Because the last time I checked, even with Java installed, It would just sit at the loading screen or I just gotten a white box. 

It appeared that pogo.com requires Internet Explorer! 

But, the out of memory error message, that usually would only occur if virtual memory (the swap) was disabled.

---

