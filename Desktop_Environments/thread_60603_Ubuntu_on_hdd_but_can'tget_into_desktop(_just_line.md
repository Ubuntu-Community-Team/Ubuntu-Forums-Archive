---
title: "Ubuntu on hdd but can'tget into desktop( just lines)"
date: 2005-08-28
forum: Desktop Environments
---

### Post by sapper on 2005-08-28
Hi, 
   I burnt ubuntu iso to disc and down loaded to hdd.Everything went well loaded a few things into vavourites and closed down for the night, next day I couldn't get into the desktop, all it showed were lines.This also happened on my other machine when I tried it,so I decided to just use it on this one. I know nothing about linux and can't really use it but I would really like to learn, so if someone knows the answer to this problem" remember you must guide me through it.    Many thanks.

---

### Post by plb on 2005-08-28
could be a number of things really but I would suggest checking your log files and posting back or if your feeling lucky try reconfiguring X........ dpkg-reconfigure xserver-xorg from the command line or run xorgconfig

---

### Post by eivind on 2005-08-28
OK. There are many possible errors here.

First: Are you quite sure you have **installed** Ubuntu to your harddisk?

Second: Could you please quote for us the lines that show up? They may be error messages or the like, and may help in solving the problem.


Cheers,

Eivind

---

### Post by sapper on 2005-08-28
Thanks for your quick response but how do I do this? Remember no desktop. Do I start up in "for want of a better expression"in safe mode? as I can't remember what's what on start up .Thanks

---

### Post by plb on 2005-08-28
What exactly happens.......do you get these lines when gdm starts(login screen) or after...... see if hitting cntl + alt + backspace drops you down to the command line and try dpkg-reconfigure xserver-xorg if all goes well type startx

---

### Post by sapper on 2005-08-28
I can't get log in screen thats my problem.Please remember you are talking a foreign langauge to me, I supose I should buy a book " linux for idiots" if there is one.

---

### Post by plb on 2005-08-28
try what I mentioned in the previous post to see if you can get to a command line

---

### Post by sapper on 2005-08-28
eivind,
         I'm sorry I missed your post. Ubuntu is definitely on my hard drive, I've worked in it"visited web sites". I have windows xp pro and i've partioned 20 gb for ubuntu and it has worked but the minute I close down and start up again, no log in. The lines are ie: bad reception on tv and worse," no thats not good enough" it's either a dark blue with white and red lines, or yellow,green and blue going crazy. Hope that helps

---

### Post by sapper on 2005-08-28
plb,
     I went into recovery mode and typed your suggestions. Answer "xserver is not installed"

---

### Post by varunus on 2005-08-28
Wait, I'm a little confused.

You said that you had gotten into the desktop once before?  But now its not working?

That's very strange...

Does the Ubuntu liveCD (a CD boot version of Ubuntu) get you into the desktop?

Also, can you try booting into recovery mode and typing the following, word for word

sudo dpkg-reconfigure xserver-xorg

Make sure you have the '-xorg' there.

This will try and reconfigure your graphics device from the console.

What video card do you have?

---

### Post by sapper on 2005-08-29
varunus,

video card= GiGabyte nvidia G-force 6800 128MB.

It's not a live cd.

The only times I've been able to log in is when I've reformatted my partition and reloaded Ubuntu and not always then.

I followed your instructions and was doing nicely untill I came to the select colour bits (16,24) press ok and then I come unstuck because I have to give it some command or other at the prompt.

---

### Post by varunus on 2005-09-04
OK, an nvidia card...have you tried to follow these instructions?
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

This should fix your graphics problems, I think.

(And you can do all of that from a console if you can't get into graphical mode; so choose rescue mode if you have to.  Just replace gedit with nano in the instructions.)

---

