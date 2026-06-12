---
title: "Korean Keyboard"
date: 2009-06-04
forum: General Help
---

### Post by Weohstan on 2009-06-04
As a new user of ubuntu (9.04 jaunty) using gnome, I am trying to install Hangul - the Korean script - so that I can switch between English and Korean. (I don't want Korean as the default language.) 

I installed the available Korean keyboard via "System>Preferences>Keyboard>Layouts>Add>Korea, Republic of." I also installed the language software via "System>Administration>Language Support>Add/Install Languages>Korean."

However, I notice after selecting "System>Preferences>Keyboard>Layouts>Add>Korea, Republic of," it gives me a preview of the keyboard that it will switch to. The problem is that it isn't Hangul! It's still Roman text. 

The other problem is that of swtiching between the "USA" keyboard setting and the "Korea Republic of" setting. It just does not seem to switch. Even after I hit the two "alt" keys together (the default setting for switching the language" -- or when I manually click on the Keyboard indicator to try and change it -- it still reads "USA." 

A little help?

---

### Post by Weohstan on 2009-06-04
Oops, nevermind the issue of switching the layout. I can just click on it, and it will switch. That's no problem.

---

### Post by domino1241 on 2009-06-05
bump

I am also having trouble getting my keyboard to type in Korean.  The preview picture of the keyboard is Roman letters, as Weohstan pointed out.  Pressing the Hangul key does nothing.

Ideas?

Ubuntu 9.04 - liveCD

---

### Post by domino1241 on 2009-06-07
Anybody?  Please?  Are there no Ubuntu users who type in Hangul (Korean alphabet)?  I am spending the summer in Seoul, where everybody uses IE6 and hasn't even heard of Firefox (much less Linux), and they marveled at the liveCD.  But how are they supposed to take Ubuntu seriously if it cannot type the Korean alphabet?

Thanks!

---

### Post by domino1241 on 2009-06-08
Oy vey,

Well I figured it out, for those who are interested.

[LIST=1]
[*]In a terminal, type ```
sudo apt-get install nabi
```
[*]Open or create the file .gnomerc in your home folder
[*]Enter the following lines in /home/USER/.gnomerc
```
export XMODIFIERS="@im=nabi"
export GTK_IM_MODULE=xim
```
[*]Go to System->Preferences->Startup Applications
[*]In the Startup Programs tab, click Add
[*]For the Name field, type Nabi, for the Command field, type ```
/usr/bin/nabi
```
[*]Log out of your session then log back in
[/LIST]

Thanks to tiger338 at [http://ubuntuforums.org/showthread.php?t=30517#3](http://ubuntuforums.org/showthread.php?t=30517#3) for the solution.

---

