---
title: "Lost wireless -Mini 9-"
date: 2009-03-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sirebral on 2009-03-11
I was trying to help vickroxy and I went into admin > preferences and found this, prepare for shipping software.  So i ran that.  It said the OEM config would restart.  I just filled it in again and I seem to have everything I had before (no luck on the clean format), but now my Network doesn't show up in my Notification Area and I am not connected via wireless, nor can I.

What gives?  Anyone?

---

### Post by sirebral on 2009-03-11
BRICK!

Not completely but when it comes to network my Mini 9 is a BRICK!  Not sure if I autoremoved some Libraries or if the OEM prepare for shipping software screwed my config 9 ways to sunday.

Looking at Xubuntu.

---

### Post by jaqrah on 2009-03-11
How unfortunate!  What happens if you re-install with Dell disk?  I was under the impression that would restore your mini back to factory settings.

---

### Post by ugm6hr on 2009-03-11
Presumably you had a non-Dell OEM installation.

Prepare for shipping wipes all the users settings, and creates a temporary user "oem" which allows the receiving customer to choose their username and password.

Making system setting changes when you don't know what you are doing is perhaps not the best idea.

---

### Post by sirebral on 2009-03-11
> **ugm6hr said:**
> Presumably you had a non-Dell OEM installation.

Prepare for shipping wipes all the users settings, and creates a temporary user "oem" which allows the receiving customer to choose their username and password.

**Making system setting changes when you don't know what you are doing is perhaps not the best idea.**

No. I had the DELL install.  The bolded part kinda hurts my feelings, though it is true.

I actually fixed the problem.  I had to mess around with the settings a little.  My biggest problem was the wireless driver never started up in use, so my wired connection was default.  I changed the wired connection to 'Automatic' and then enabled my wireless driver.

It works now.  The OEM button is GONE.  What was the purpose of putting that on a DELL install anyways.

BTW .. Tried XUBUNTU.  Looks terrible though. :(  Everything is just LARGE. :(

---

### Post by armandh on 2009-03-11
I love OOTB 8.10 on my mini9

---

### Post by sirebral on 2009-03-11
> **armandh said:**
> I love OOTB 8.10 on my mini9

Trust me I am becoming very jealous.  Did you know that the network is highly dependent on my Maximus?  If that doesn't run I seem to drop connection.  I am still trying though.  I hates maximus.

OTH, I want to support DELL int heir decision to run with Linux.  I have become a solid linux fan (since 7.10). While the first Linux OS I brought from them was kinda crappy, i still kinda liked it.

I also played around with Xubuntu.  I wish it looked better.  When it comes to system resources though, the two appear to similar. I am still running my own tests.

---

### Post by anjilslaire on 2009-03-11
> **sirebral said:**
> 
BTW .. Tried XUBUNTU.  Looks terrible though. :(  Everything is just LARGE. :(

Yup, thats what happened to me, too. I went to Ubuntu 8.10 and everything is fine.

Oh, I have the netbook remix installed, without Maximus. Everything is fine.

---

### Post by ugm6hr on 2009-03-11
Unfortunately, the number of configuration options is just a little *too* inviting to meddle with in Linux.

My advice: know how to undo changes before you make the change.

---

### Post by sirebral on 2009-03-11
Thanks for the installation tip, armandh.  Thanks for the help learning about Xubuntu, anjilsare.

I broke down and installed 8.10.  I am currently finishing updates (268!! Whew!) and setting up the few things that need it. (Sound.)

Next time DELL tries to close their source I hope they leave customizing up to the customer.  It was the maximus software that killed it for me. :evil:

---

### Post by jaqrah on 2009-03-12
Sirebral

Just out of curiosity..how are you finding 8.10?  Haven't seen any posts lately?

---

### Post by sirebral on 2009-03-12
Overall: You wouldn't notice the difference.  The 8.10 OS works just the same with the added functionality.

One thing I have noticed
Booting with 8.10 hangs momentarily near the third bar.  Not sure why.  During installation the software did a long time with drivers, so my guess is the new monitor size.

---

### Post by anjilslaire on 2009-03-12
Time to change the sig, eh sirebral?

---

### Post by armandh on 2009-03-13
> **sirebral said:**
> Overall: You wouldn't notice the difference.  The 8.10 OS works just the same with the added functionality.
One thing I have noticed
Booting with 8.10 hangs momentarily near the third bar.  Not sure why.  During installation the software did a long time with drivers, so my guess is the new monitor size.

mine does it too
I suspect now that there is no longer a custom kernel it does the complete hardware sorting out each boot.... video drivers come in to play way after the crawler in my experience

how does one get verbose mode boot????

---

### Post by sirebral on 2009-03-13
> **anjilslaire said:**
> Time to change the sig, eh sirebral?

hehehe.  I forgot all about that.  You are correct.

> **armandh said:**
> mine does it too
I suspect now that there is no longer a custom kernel it does the complete hardware sorting out each boot.... video drivers come in to play way after the crawler in my experience

how does one get verbose mode boot????

I am thinking the exact same thing.  Not sure the answer to your query though.

---

### Post by ugm6hr on 2009-03-13
> **armandh said:**
> how does one get verbose mode boot????

Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```

Delete the words **quiet** and **splash** on the kernel line near the bottom.

PS: Make sure you don't do anything else, unless you know what you are doing, since a single mis-edit can stop you booting.  Consider keeping a backup of this file before editing:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp
```

---

