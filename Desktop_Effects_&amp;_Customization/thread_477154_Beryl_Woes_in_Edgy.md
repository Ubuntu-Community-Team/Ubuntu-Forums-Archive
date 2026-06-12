---
title: "Beryl Woes in Edgy"
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by RelativelyQuantum on 2007-06-18
Quite simply: How do you install Beryl in Edgy???

I've been trying for days now and have been met with only brick walls and dead links. This one's my favorite:

[http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)

I'm fairly sure that one won't help me. Is there anything I'm missing? I've been on countless how-tos and Beryl-related posts, but have turned up nothing. I know I *can* get it to work; I just don't know *how.* I would rather not upgrade to Feisty again after a few unfortunate happenings, culminating in my hard drive being wiped and the loss of three operating systems.

Can anyone help me out? This is a big dilemma, but one which I'm sure I can fix with a little advice to point me in the right direction. Any advice, any at all, would help a great deal.

Cheers,

RelativelyQuantum

---

### Post by SishGupta on 2007-06-18
It sucks that you have been having so much trouble. There official wiki is down for some reason (maybe because of the beryl and compiz merge).

The link pasted above has the repo lines you need to paste, that is why so many people linked you to that site.

here are the steps you need to take:
at terminal:
1. sudo gedit /etc/apt/sources.list
2. paste in the following lines
```
          
deb http://ubuntu.beryl-project.org edgy main
deb-src http://ubuntu.beryl-project.org edgy main

```3. save and close
4. sudo apt-get update
5. sudo apt-get install beryl beryl-manager emerald-themes
accept all dependencies
6.  go to applications>system tools>beryl-manager

beryl should start, if not use the beryl-manager icon on the tray and you should able to figure it out.

You will need the proprietary drivers installed if you are using an nVidia card, and I am not sure what the status is on ATI anymore.

Futhermore, though i wrote the directions out myself, 90% of all questions for ubuntu users can be answered on [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)
including [complete instructions (READ THIS!!! TOO) ]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29")
Make sure you scroll up and down as there are instructions for ATI users and XGL needers.

You also may have better luck if you run feisty as edgy is out-of-date and may not be as easy to run beryl on.


---

### Post by RelativelyQuantum on 2007-06-18
Thank you so much! This really helps; I thought I was lost there for a while. Looks like I can use Beryl after all! :D

---

### Post by RelativelyQuantum on 2007-06-19
Ha! I used the tutorial on the link you sent me, and had it installed within ten minutes :D

When I opened the manager, however, my effects disappeared. Beryl is still in one of my startup programs, but I have no desktop cube, wobbly windows, etc.

Any idea what could have caused that?

---

