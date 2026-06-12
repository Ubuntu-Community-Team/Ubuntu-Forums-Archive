---
title: "KDE goes nuts"
date: 2007-03-22
forum: Desktop Environments
---

### Post by Peque on 2007-03-22
Hey Guys. 

I have an IBM X60s with intel i945 
I have been running dualscreen for long time without any problem. 

I have a fingerprint scanner - and got that to work the other day.But now my KDE seems to be totally screwed. Follow this wiki [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader)

When I boot the machine - and goes to TTY1 i can se that the machine loads a VESA driver??? Nowhere in xorg.conf says anything about vesa drivers. 
I cannot use my 2.screen - first of all its 440X680(or so)  and when I move a windows - its getting stuck in the middlke between the 2 screens. 

I have allso deleted my xorg.conf and used my original from the time where it all worked! But still the same result - I would really like to use the fingerprint scanner - But rather want a normal KDE Dualscreen. 

Have anybody any ideas??  Caurse I cannot find where X are loading the vesa Driver and Why ????

---

### Post by g8m on 2007-03-22
First, I dont think this has anything to do with KDE.

Check /var/log for errors. Messages is good place to start, but check Xorg.0.log first. And .xsessions-erros in the home folder might give some clues.

---

### Post by Peque on 2007-03-22
I have tried that - but none errors was discovered. 
I added and new user - and for him everything works just fine - So I' ll deleted all my .kde files Xauth***** .xsession files in my homedir and rebootet - pling - then it worked again. 
But how can Xorg run - when /etc/X11/xorg.conf is deleted ???  how is it possible to get Desktop running without this file ? 
Caurse one of my tries was to delete this file and reboot the machine for clearing anything cached ? but it just went straigth into windowmanager!

But thanks anyway.

---

