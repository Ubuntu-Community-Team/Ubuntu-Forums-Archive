---
title: "[SOLVED] KDE - Setting for Mac/Windows/Linux style desktop"
date: 2008-06-04
forum: Desktop Environments
---

### Post by Muffy on 2008-06-04
I've been using Ubuntu for a fair while now. Recently I wanted to change my desktop to feel more like a Mac by installing KDE. 

KDE installed fine, and upon first boot I went through a setup wizard. During this wizard I was asked what type of desktop I wanted, there was 4 options: Mac style, Windows style, Linux style, and something else. I chose Linux style out of curiosity. It wasn't what I was after. 

I have been unable to find where I can change this option outside of the wizard. Can anybody help me? Thanks.

---

### Post by Xiong Chiamiov on 2008-06-05
Which KDE did you install (3.5.9, 4.0, 4.1)?  And how did you install it(repos, source)?  I haven't seen that option when I installed KDE, though I haven't installed it fresh in a little while.

That said, I think it'd be easier to do so with GNOME, using the Mac4Lin project.  Just follow [this guide]("http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac").

---

### Post by Naegling23 on 2008-06-05
I've never heard of mac/windows/linux style, thats new to me, but I've had kde running for a couple of years, could be a new thing.

Go to system settings.

Your going to need to change a few things to get what you want.  Just poke around in desktop, window managers, and such until you get the look you want.  If you dont like all of the options, [www.kde-look.org](www.kde-look.org) has some more stuff for you.  All the settings are there, but I dont know exactly what ones you want to change, nor do I exactly remember where they all are (Im at work atm).  

As an aside, I find it interesting that you installed kde to get a more mac like look.  usually gnome is considered more mac like, and kde more windows like.  But I hate that argument, since my kde desktop looks nothing like either of them....ah, configuration!

---

### Post by joninkrakow on 2008-06-06
> **Muffy said:**
> I've been using Ubuntu for a fair while now. Recently I wanted to change my desktop to feel more like a Mac by installing KDE. 

KDE installed fine, and upon first boot I went through a setup wizard. During this wizard I was asked what type of desktop I wanted, there was 4 options: Mac style, Windows style, Linux style, and something else. I chose Linux style out of curiosity. It wasn't what I was after. 

I have been unable to find where I can change this option outside of the wizard. Can anybody help me? Thanks.

I don't remember this option myself, but I know that you can turn on a Mac-like menu bar, where in all apps (KDE apps only, unfortunately) share the same menubar at the top of the screen, like in the Mac OS. In 3.5, this is in the "Desktop System settings, under "Behavior". At least on my computer. I've discovered that sometimes these things can look differently...

The option you want is under the option, "Menu Bar at top of screen, and the option is "Curren applications menu bar (Mac OS-style)" 

That will get you the menu bar. 

Second option I would change is for the single-click-to-open-things in Konqueror, desktop and Dolphin. That's found, oddly enough, under "Keyboard & Mouse", in the Mouse tap, under "Icons". Next, I would make sure that "Visual feedback on activation" is on. 

Thirdly, Go to "Appearance" under "Look & Feel" and find "Window Decorations" tab. Inside that, find the "Buttons" tab. In there, you can re-arrange the order of your window-top buttons to match the Mac's of "Close, minimize, Maximize, Title, Menu". 

Other than that, I can't think of other things you can do to create a more Mac-like environment, other than skinning, which, on my computer at least, is not trivial. I just stopped with those three items--and undid the menu trick, because it gets messy when you start working with non-KDE apps. :-)

-Jon

---

### Post by F4l3 on 2008-06-06
if you want install kde3.5.9: sudo apt-get install kubuntu-desktop
if you want install kde4.0.4: sudo apt-get install kubuntu-kde4-desktop
if you want install kde4.1b1: 
 - sudo nano /etc/apt/sources.list
 - ADD: deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main 
 - Ctrl + O
 - Ctrl + X
 - sudo apt-get update
 - sudo apt-get dist-upgrade
 - sudo apt-get install kubuntu-desktop

---

### Post by Muffy on 2008-06-15
Thanks for the help guys.

I realised that KDE wasn't what I was after.  I just installed Avant Windows Navigator and now I'm happy. 

Cheers guys.

---

