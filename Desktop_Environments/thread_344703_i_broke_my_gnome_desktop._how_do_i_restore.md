---
title: "i broke my gnome desktop. how do i restore?"
date: 2007-01-23
forum: Desktop Environments
---

### Post by jammodotnet on 2007-01-23
I've been a member of this forum since April 10th, 2006. This is my 2nd time installing Ubuntu. This time, I have been more successful in getting it to properly dual-boot with XP Pro.
I even went so far as to properly partition my hard drive and I now have a partition called SHARE, which is FAT32, and I use to share files between my two OSes.

I am still far from considering myself even a Beginning user. So please bear with me as I explain my problem today. :(


Two days ago, installed Edgy 6.10.
I followed this initial installation with some mistakes, reinstallations, etc.
then installed Automatix2 and a few needed apps. Firefox with needed extensions (i backed up my Windows profile + bookmarks, too!). Also got Bluefish, and I even got XAMPP working. localhost works just fine, i got some neat wallpapers.


I followed a short total-newb tutorial on how to add transparency to the taskbar panels.
(after a thorough search through my history, here is the t00t: [http://www.mbhoy.com/19-01-2007/howto-simply-stunning-linux-desktop](http://www.mbhoy.com/19-01-2007/howto-simply-stunning-linux-desktop))

The toot says to download: gnome-hideseek_0.6.0-1getdeb1_i386.deb which I did. I launched the application, then, our apartment lost power for a second while in the middle of configuring HideSeek application.
I have my PC, printer & monitor plugged into a power strip, but still suffered from the hard crash and restart.

NOW?!
hhmm, it's scary. My top and bottom panels are empty. Well, actually, the bottom has the Ubuntu logo (same positioning as MS Start menu), and the little icon of an ExitDoor? is at the top center. Those are the only 2 visible icons, aside from my desktop.
The desktop has the trash can icon, as well as my home folder.

I right-click on either top or bottom panel, I get no sub-menu.
I can single or double click anywhere or any of the 2 icons on the top or bottom panel, I get nothing.
I was able to navigate to File System directory and search for Firefox, which is how I brought up the forum. I have no idea how to bring up terminal.

This other thread: [http://ubuntuforums.org/showthread.php?t=333090](http://ubuntuforums.org/showthread.php?t=333090) **How do I completely delete a desktop environment's settings? [Resolved]** sounds abit like what I would need to do, but without terminal, I am at a total loss.
I'd hate to resort to my previous proven-true method of reinstalling my new beloved OS. ](*,)

---

### Post by renzokuken on 2007-01-23
you dont need the terminal within gnome. when you boot up and get to the GDM login screen, press the follwing keys

Ctrl+Alt+F1

this will take you to a command line interface screen where you can login and perform any command line/terminal based operations without gnome or any desktop manager.

hope this helps

---

### Post by jimbren on 2007-01-23
You should be able to get to a console login from GDM, or a failsafe.  From there, you would want to go through the steps outlined in the How do I completely delete a desktop environment's settings? article you cited.  

Fear not--a few minutes work and you'll be good to go.

Please respond if you have a hard time getting to a console window.

jimbo.

---

