---
title: "Urgent. How to start Linux?"
date: 2006-01-08
forum: General Help
---

### Post by Rasymas on 2006-01-08
Sorry guys and gals not for searching the forum for excisting topics. Sohere's my problem!

I've installed Linux (like from the 4th time. Lost all my stuff I had) but that's not a big problem. The thing is I don't know how to start Linux! While booting, some question pops up.

username (or log in) then I enter my log in name
Password (******) :)

Then some words appears, then

arnoldas@ubuntu: ~$

WHAT TO DO???

Thanks in advance :)

---

### Post by Tiede on 2006-01-08
What I understand from your post is that you are in a terminal instead of a normal graphical one. This should not happen, unless you did a basic or server install OR your Xorg is broken.
To figure out which one it is, do this at the prompt you have after putting your password:
```
 X 
```
and report what happens.

---

### Post by Gowator on 2006-01-08
[QUOTE=Rasymas]Sorry guys and gals not for searching the forum for excisting topics. Sohere's my problem!

I've installed Linux (like from the 4th time. Lost all my stuff I had) but that's not a big problem. The thing is I don't know how to start Linux! While booting, some question pops up.

username (or log in) then I enter my log in name
Password (******) :)

Then some words appears, then

arnoldas@ubuntu: ~$

WHAT TO DO???

Thanks in advance :)[/QUOTE]
It sounds like your graphics are not configured ...
Do you know what graphics card yuou have? 

If you type 
lspci -v |more 
it will scroll lots of stuff off the screen as you press space and you can read the exact name/model of the graphics card.  

There are quite a few paths to take such as editing the config file by hand or running various utilities or running a live Cd and copying the settings.  If you have a fast internet connection downloading a live CD might be easiest and let you work in a graphical environment.  Since ubuntu has for some reason failed to autoconfigure then I would suggest a different live CD (kanotix has very good detection) [www.kanotix.com](www.kanotix.com) or a non Debian based one like slax or pclinuxos.  

If this works you should be able to access the internet and cut and paste stuff to get it working or if your connection is really slow you can try and copy /etc/X11/xorg.conf somewhere you can see from Windows and post it...
or you cvan try the xorg autodetection ...

startx --configure

this will make a file and you follow the instructions to see if this file works.  
if it does yopu can copy it

---

### Post by Rasymas on 2006-01-08
I finally installed Linux properly. And I'm very happy with that, but now I have another problem. That is when I load up Ubuntu, my mouse pointer ain't moving, just stands in the middle of desktop. Any soliutions? ;-)

---

### Post by Jedeye on 2006-01-08
Are you using a USB mouse, Wirless?

---

### Post by Rasymas on 2006-01-08
I have some pretty old A4 Tech mouse it's neither wireless nor USB! ;)

---

### Post by Gowator on 2006-01-09
How did you fix it?

The mouse problem is likely a confgi issue on the same file (xorg.conf) so if you can say how you finished the install it will help people help you.

---

### Post by Rasymas on 2006-01-09
So here it is. After crazy base system install, I reinstalled Ubuntu (this way -> when you start a install you press F1 and then proceed, dunno how it's called) so everything works fine, except for mouse. I've configured internet with keybord, pretty crazy thing to configure damn DSL! I brought my friends USB optical mouse, works fine! If I didn't tell you, my mouse is conected VIA COM1. ;)

---

### Post by kipman725 on 2006-01-09
I can't get serial mice to work with ubuntu ethier, usb or ps/2 work fine though and are very cheap.

---

