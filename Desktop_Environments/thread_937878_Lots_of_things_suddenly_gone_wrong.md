---
title: "Lots of things suddenly gone wrong"
date: 2008-10-04
forum: Desktop Environments
---

### Post by Stevil on 2008-10-04
Hi, 
a whole bunch of things suddenly started going wrong on my desktop. I'm pretty new to Ubuntu so I have no idea what is going on. I am running Ubuntu 8.04 GNOME. :confused:
Beforehand I installed Desktop Drapes (which I have since removed), some packages for R (a statistics program), g++ and fortran. 
Things were ok for a while, but then suddenly:
- nautilus was telling me that I had 0 bytes free, when I had over 1.5GB a minute before, so I cannot do anything including writing documents because the computer says I have no space left. 
- After that, Firefox started to go weird: all my bookmarks disappeared and the google search bar does not work. 
- A lot of my desktop applets, such as Tomboy, have disappeared and can not be put back on. It comes up with the error "The panel encountered a problem while loading "OAFIID:TomboyApplet"."
- Sometimes when I open Firefox or OpenOffice the window is filled with coloured lines and nothing happens
- Applications frequently crash
- when i click on the shut down, red square icon both top and bottom menu bars disappear
- Documents,Pictures,Videos,etc disappeared from Places menu and in the sidebar of Nautilus
- Applications menu does not work
- Screen resolution gone to 800x600
- Menu menu items don't work, eg can not get into Sessions or Main Menu
- Many of the items in the Menu have gone, eg Screens and Displays
- desktop effects have turned off and graphics drivers don't work
- Probably more stuff that I have just not found yet. 

Like I said, everything was working fine until Nautilus said that I run out of space. I have deleted things, but this does not change anything. 
Also things are seeming to get progressively worse. For instance, I was able to access the Applications menu until recently. 
I have tried loading an earlier kernel, trying different users, running in recovery mode and nothing seems to change. 

Does anybody know what is wrong? Is it from something that I installed? I have never had any problems before and now things are totally messed up. It's like my whole system is decaying. Somebody please help!! 
Thankyou in advance!

---

### Post by Stevil on 2008-10-04
Still getting worse!
It's only been a few minutes since I last updated the things that are going wrong and since then I am no longer able to get into Places or System from the Menu and I think the resolution has gone even lower than 800x600.

---

### Post by Stevil on 2008-10-04
I tried to fix the problem the way some have done when their panels disappear:
removed .gnome, .gnome2, .gconf, .gconfd, .metacity from home folder. I backed them up on a USB. Then I restarted GNOME with Ctrl-Alt-Backspace and I could not log back in to my user at all. It says that my session lasted less than 10s and I should try failsafe, which I did I got the same message. 
Luckily I have another user which works, I gave it administrator privelages, and I tried to move the folders I removed back in to my home folder, but because it thinks that disk space is full it will not let me.

---

### Post by linux2.6.24-19-generic on 2008-10-04
Sounds pretty bad.  I would format the drive and re-install the OS.  I would create 2 partitions.  Use one as an experimental system, a playground that you can install whatever and try new things.  And only do stuff on the second system that you have experience with.

This might sound drastic, but it will probably save you hours of distress.

Just my 2 cents, I would get other opinions before you follow my suggestion.

---

### Post by Anlace on 2008-10-05
Just a thought for troubleshooting.  Maybe you are looking at a hardware failure, possibly the video card or hard drive.

I've seen hardware failure cause all kinds of strange, inexplicable behavior in Ubuntu similar to what you have described.

---

### Post by KernelKen on 2008-10-05
I have started getting the same problems on my laptop.  
No space left on hard drive.
Can't shutdown I lose the top and bottom bars but it doesn't shutdown
Lost my bookmarks.
But I didn't load in new programs before it started happening. It was at least a week or more before I loaded any other programs.  
I am dual booting and vista is not experience any problems.
Any other ideas.

---

### Post by bangkok on 2008-10-05
although i am not having as extreme problems i have some similar issues with two different desktops running hardy on both of them (i am actually having the exact same problems on both of my desktops). 

apps i am running seems to slow to a crawl or stop responding and eventually nothing on the desktop will respond. i then have to ctrl+alt+f2 to shutdown -r now for re-boot and then everything is fine again for awhile.

before things totally freeze up on the desktop i will usuaully notice pidgin is the first app to slow/stopping responding and a force quit is usually required. it starts up again ok but usually will freeze right away again and then the rest of the desktop seems to follow.

actually something i regularly notice happening before the desktop and apps begin freezing is that i am unable to play mp3s on either exaile or gplayer. i play lots of mp3s and when things are about to go south i will notice that mp3s i load for playing will load but not play at all. if i try to use skype or anything requiring sound i am pretty sure that is also unresponsive... the app starts but no audio.

i like using pidgin but started looking at using another IM client to see if the whole desktop problem continues or not, but i am not really liking much of anything else available for IM.

this is getting pretty annoying and i am not sure where to start looking. i can't see how two different desktops can have the same hardware issues creating the almost exact same problems.

i haven't noticed any problems on my laptops but i run xubuntu on those so could there be something flaky with gnome going on here?

bangkok

---

