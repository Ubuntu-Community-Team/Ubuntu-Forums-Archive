---
title: "kde4 desktop launch"
date: 2008-04-02
forum: Desktop Environments
---

### Post by jimbo99 on 2008-04-02
I installed KDE 4 shortly after it was released and thought basically that it was utterly messy and extremely buggy.   After doing some configuration with it I switched back to the gnome desktop.  I then had some time away and went back to revisit hoping there were things I could learn from it for the time when they polished it up some.  After spending a short period of time with it I moved back to gnome.

After learning today that KDE 4.0.3 had been released I thought I'd take another look at the desktop.  Things seem to have gotten worse over time even though I have not used it.  I believe that KDE is headed the right direction but are a sorry sort when it comes to execution.

After changing my log in session to KDE 4 (temporary) I found that nothing I could do would allow me to launch an icon from my desktop.  Some of the drive Icons should have represented mounted volumes and mounted drives but they were generic folders.  I could not open the folders.  I could not open anything at all.  I could right click on the back ground and choose the run command and execute that way and I could execute programs from the KDE menu, but none of the icons on the desktop worked.

ANY IDEAS?

---

### Post by jimbo99 on 2008-04-03
Still waiting on any ideas someone may have.

---

### Post by benerivo on 2008-04-03
I believe this has something to do  with how the Desktop is managed by kde4. I think one of the concepts of kde4 is that it doesn't consider the desktop as a folder where normal files and links can be stored (i have experienced this myself as I found I can not drag a file in to the console). In kde4, the desktop seems to be desiigned only as a place for 'widgets' rather than a folder location. Maybe someone who knows more about kde4 could shed some light on why this is?...

---

### Post by jimbo99 on 2008-04-03
It used to work.  I was able to open folders and launch programs from the desktop.  I also was able to see mounted volumes (local and remote) as drive icons.  Now i can't and right clicking on these desktop icons only shows 2 menu entries.

I tested that I can run programs from the kde 4 run dialog and from the new KDE 4 menu.  It is just that the desktop is not functional any longer, tho the widget in the upper right corner of the desktop to add more widgets does seem to function.

I like the look of KDE and I like the concept, but it is massively buggy.  Just some ugly programming I would guess.

I also had a situation where the desktop background could be accidentally moved and put out of kilter.  I couldn't move it back once it became moved (offset from being squared in the monitor).

Just some weird weird things happening.  This latest that keeps me from launch programs is quite irritating.

---

### Post by jimbo99 on 2008-04-04
I have found some partial solutions to this issue.  I can now access folders by double clicking on them.  I found that one of the repositories was not enabled in my software sources and when I enabled those I was able to do some updates.  Those updates solved some of the issues, but many still remain plus a perplexing problem.

1) why did this just start happening.  I hadn't used KDE4 in a long time and there were many updates that took place over that time related to Ubuntu.  Did some libraries become out of date and synaptic didn't show any conflicts or broken packages?  I think this is interesting and it would be nice to have broken apps show no matter what.

2)  There are icons on the desktop that represent folders, files, etc.  I can open a folder but I can't drag and drop a file into the open folder from the desktop.

3)  When I got to the desktop the icons were all messed up, randomly strewn everywhere.  When I moved my cursor over them this sort of transparent white box normally would surround the icons providing me with choices such as configure, a red X to close them, etc.  My question is:  where do these go if I click the red X because they don't appear to go to the trash.  In fact, the trashcan on the desktop can be opened like you would open a folder but there is no way to empty the trash can.  So, the icons I remove from the desktop using the red X disappear but they don't go to the trash.  A couple of them have returned on the next boot.  Where do these go?

4)  I can't find the start up items list to stop certain programs from loading when I log into KDE4.  I searched the settings manager and selected the option to start without any startup items but they still start up the next login.  I want to stop the start up so they don't interfere.  Under Ubuntu with gnome there's an application that allows you to work with sessions (apps that you start when you log in).  Very perplexing.

5)  I don't seem to be able to multiselect icons off the destkop.  I can click on a black area of the desktop and size a selection rectangle but I find no icons get selected.

6)  I can't find the option to align icons.  There's one option for align horizontally and another for vertically but I want to align against a grid or against the selection.  I see nothing to help me do that.

7) Because some things are auto started I have to move or resize the panel where the kde menu isits.  Then when I try to resize it back it doesn't fit right in that location.  There's a white bar at the bottom of the screen.

8)  When i try to create a multi desktop using the pager that doesn't work either.

There's a ton more, but if someone could answer just some of these it would help considerably.

---

### Post by jimbo99 on 2008-04-04
Had some interruptions earlier so I didn't have the time to complete the various issues that I've been having.

A few more are:

Even though KDE4 loads and I get the pretty transparent overlays, etc., there are no compiz type effects unless I load compiz --replace.  When I do that the programs such as the clock applet has residual graphics such as the second hand being repeated over and over.  Given enough time the desktop background will become visually distorted.  Very wierd looking desktop.

The task bar at the bottom blinks clear and then fills with black (the default color).

Icons which represent permanent network share mounts are not shown.

When i bring up a dialog box for properties or something like that the top border of the window (the title bar) with all the controls is up beyond the top of the monitor.  I have to alt+mouse to move it down.

These are just some of the things I noticed in the first 30 minutes of using the desktop.  I am wondering how any of this still exists and why a lot more of this isn't being discussed on these web forums.

Also, I can't play sound out of my VLC or mplayer, but I can hear system sounds.

My installation is not custom and I have done very little over the past 2 years except just use it to do what i normally do.  I have stayed away from adding odd things or any sort of technical customization with the exception of loading things like Avant-Window-Navigator.  Even so, I am not using it in conjunction with the KDE4 desktop.

Any ideas would be helpful.

---

### Post by benerivo on 2008-04-04
Generally, I have the same functionality problems, but none of the graphical glitches that you get, which makes me think that kde4 DESKTOP still has some useability issues, and also that your hardware/xorg setup is causing problems. I also had graphical issues, although 4.0.3 has completely fixed them.

When you say you can hear system sounds but nothing else, do you mean you can hear the kde4 desktop effects such as the opening windows effect, and applying settings effect, and yet there is no 'program audio'? 

What programs are loaded during startup that you don't want?

You can have compiz load at startup rather than loading it manually. Also, the compiz settings manager has a setting that forces windows to open entirely within the screen rather than losing the top half.

Can you post a pic of the panel problems you have.

---

### Post by jimbo99 on 2008-04-04
Yes, I know I can have compiz load automatically at statup, but unfortunately I can't find where to set it.  

Part of my question was where to I set this?  What program do I use?  In Ubuntu with gnome I set it with the "sessions (gnome-session-properties)" program.  Very simple, very straightforward.

---

### Post by benerivo on 2008-04-05
It's done in your home folder (I don't think kde has an equivalent to gnome). Look in ~/.kde4/Autostart. You can drag a file such as /usr/bin/compiz in to this folder and it will give you the option to paste a link.
> When i try to create a multi desktop using the pager that doesn't work either.I think this is because compiz and the kde desktop controls have never worked very well together. I'm using compiz and kde4, but i have abandoned the pager/desktop controls, and instead use the 'General Options' in the compiz settings manager to control multi-desktops.

---

### Post by jimbo99 on 2008-04-07
I really haven't addressed pager issues for most of my post.  That's not a big deal.  I was asking for other information.  The pager issue just isn't big enough.  So, how about answers to the other questions?

---

