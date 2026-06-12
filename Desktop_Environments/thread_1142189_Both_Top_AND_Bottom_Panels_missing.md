---
title: "Both Top AND Bottom Panels missing"
date: 2009-04-28
forum: Desktop Environments
---

### Post by mromblad on 2009-04-28
I am not sure how it happened. I logged in fine and only my desktop showed. I was barely able to get into firefox. I have no where to click to add a panel.

any help is much appreciated.

I also do not know how to get into a terminal other then pressing ctrl+alt+f2.

---

### Post by andrea000 on 2009-04-29
I dont know what version you run but i know up to
8.10 this should work just never tried it myself.
from the terminal

To get all your default panel items back, simply 
open terminal alt F2 and type in gnome-terminal 
when you get a terminal type in

sudo apt-get install ubuntu-desktop

---

### Post by mromblad on 2009-04-29
installing ubuntu-desktop worked. that is odd that it just went away like that.. Thanks!

---

### Post by andrea000 on 2009-05-01
no problem glad to help and welcome to ubuntu

---

### Post by fourbit on 2009-05-03
Thank you. I too had that problem and this has done the job. ;)

I couldn't get the terminal to show with alt+f2 . I used ctrl+alt+f2 and then used the command you provided. 

I then restarted the machine. And, all has returned.

I too am curious what happened to begin with.

---

### Post by d3v1us on 2009-05-18
<Ubuntu Desktop 9.04>

for me the panels just didn't appear, so I'll need to add that to the startup applications.  if you can right-click the desktop and create a launcher, name it whatever and for the command type:  gnome-panel

double-clicking the new icon should load the top and bottom panels.

= d3v1us

---

### Post by 78ufzniyE4 on 2009-05-28
hi today i just had that problem i think i know why that happend after that girl replyed you must have acsedently removed the ubuntu desktop i wanted to remove evolution because i downloaded thunder bird so one of the packages had the rely on ubuntu desktop but i deleted that package along with ubuntu desktop sooooooo thank you so much lady i dont know what to call you :)[http://ubuntuforums.org/images/smilies/icon_smile.gif:D:popcorn:;):(](http://ubuntuforums.org/images/smilies/icon_smile.gif:D:popcorn:;):()

---

### Post by mcduck on 2009-05-28
> **linuxbrother11 said:**
> hi today i just had that problem i think i know why that happend after that girl replyed you must have acsedently removed the ubuntu desktop i wanted to remove evolution because i downloaded thunder bird so one of the packages had the rely on ubuntu desktop but i deleted that package along with ubuntu desktop sooooooo thank you so much lady i dont know what to call you :)[http://ubuntuforums.org/images/smilies/icon_smile.gif:D:popcorn:;):(](http://ubuntuforums.org/images/smilies/icon_smile.gif:D:popcorn:;):()

Removing the *ubuntu-desktop* package will not remove anything from your computer, it's just a metapackage used to install all the stuff included in the default Ubuntu setup. (In other words, it's empty package that has all the default stuff marked as it's dependencies. On the other hand no other package depends on ubuntu-desktop, so installing it installs all the default stuff, while removing it only removes the ubuntu-desktop package itself)

But removing *Evolution* and all it's components *will* remove important stuff from your desktop. For example Gnome-panel needs some evolution components.. (For example the clock applet is tightly integrated to evolution, as it shows your appointments and tasks from Evolution calendar.)

edit: You can remove Evolution, if you want, but be very careful when removing other evolution components.

---

### Post by 78ufzniyE4 on 2009-09-20
of topic how did you get coffey instead of bean
s:):guitar::lolflag:

---

### Post by Penguin Guy on 2009-09-20
> **linuxbrother11 said:**
> of topic how did you get coffey instead of beans
You get it once you've made a lot of posts.

---

