---
title: "I just screwed Beryl up!!  Need help quick!"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2007-07-02
Doing work on a clients laptop.  This isn't really that big of a deal because there's nothing of value on the hard drive so I can install from scratch if I have to, but I wanna try you guys first.

I was screwing around with the advanced rendering settings, and was going down the list of Rendering Platforms (Automatic, AIGLX, XGL...can't remember the other one).

Anyway, I selected XGL, and the screen pretty much froze.  The mouse will move, but the desktop is now the background color, everything is off the screen.  Just a mouse cursor (which moves, but can't click on anything).

I can access a terminal via Ctr-Alt-F2 with no problem, and actually uninstalled beryl using "sudo apt-get autoremove beryl beryl-manager emerald emerald-themes", etc.  But this XGL setting stayed on the hard drive somewhere in a conf file...

I don't know where to look or what to do to fix this.  I'd like to use the terminal window to do it.  Any ideas?

---

### Post by chris.tkd on 2007-07-02
you could try reconfiguring the xorg.conf

in your console:

sudo /etc/init.d/gdm stop (or kdm for KDE)

^this stops the desktop environment and puts you in text mode

sudo dpkg-reconfigure xserver-xor

^this will reconfigure the xorg.conf, it will ask you alot of questions but most of them are ok on default

sudo /etc/init.d/gdm start (or kdm for KDE)

^this will restart the desktop enviroment

good luck, chris.

---

### Post by stepol on 2007-07-02
In my home directory I have a Folder .beryl where I find  file : settings

Hope this helps

---

### Post by ThrobbingBrain66 on 2007-07-02
If the above doesn't work, go back to a terminal and remove the .beryl settings folder:

```
sudo rm -r /home/USERNAME/.beryl
```

This will erase all your Beryl settings, but you won't have to reinstall.

---

### Post by diablo75 on 2007-07-02
Nope.  Neither of those methods worked.  So I decided to just reinstall it.  (I just installed the OS on there like...2 days ago anyway, it's not been used.  I just had a lot of stuff installed after the fact that takes about a half our to do...  I'm a lazy guy.

But we could kinda toss ideas around about what could have done it.  Because I'm a semi-professional tech and I could easily see one of my clients wanderin' around like curious george going, "I wonder what this does?"  Heh heh.  So, if anybody else has some ideas (like a mind game, we just play "what if" for a little bit.).....

---

### Post by mitchell486 on 2007-07-02
If that happens again. You might try Ctrl+Alt+Backspace and then it should take you to the login screen. From there you should be able to select the session down in the bottom left corner, then select the one RIGHT under last session I believe. Its should be what is the default one. If that doesn't work I don't know.

---

### Post by trigun on 2007-07-02
you changed the configuration of the package beryl-manager not the beryl itself...so i think  that removing the folder .beryl don't solve anything you have to remove the folder that save the settings of beryl-manager
cheers ;)

---

### Post by diablo75 on 2007-07-04
> **mitchell486 said:**
> If that happens again. You might try Ctrl+Alt+Backspace and then it should take you to the login screen. From there you should be able to select the session down in the bottom left corner, then select the one RIGHT under last session I believe. Its should be what is the default one. If that doesn't work I don't know.

Hasn't happened again, but eariler when it did happen, I tried this.  And it didn't work.  I tried Gnome, Failsafe Gnome.  The only other one I could select was this text mode...

This may lend some help to the problem.  [This is the guide I used to install Beryl]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method").

I think what would really work is to figure out how to completely remove Beryl and its settings.  I tried this, and failed.  The settings remained, for some reason.  And after reinstalling it, I was back to square one; system locked up because it was trying to render on the XGL platform which, for some reason, doesn't play nice with my video card.

---

### Post by sgetmanenko on 2007-07-18
Had the same problem... If you force xgl rendering it messes up the system.  The first time I reinstalled, but I hate loosing all my custom setting on beryl.  Today i did it again, so i restarted X started then typed beryl-setting in the terminal, in the development tab I typed the fall back window manager command  **metacity --replace**  and so that saves me from having to reload, but i still cant get to "other" beryl settings,  the ones that you right click on the emerald for... can anyone help?

---

### Post by sgetmanenko on 2007-07-18
LOL!!! So if you do everything in the previous post, it seems that the crash handler rescues the X through falling back on metacity, at least in theory, but in reality it just unfreezes my screen with beryl still running as my window manager, so then the problem becomes getting to the emerald so you can right click on it.  Well.... just starting beryl again does it!!! The emerald comes up and you can right click and deselect XGL.

---

### Post by kid-pro-quo on 2007-07-19
I had a similar problem to this today. Every time I would try to start Beryl all the icons on my desktop would disappear, as would the window borders, and gnome would be completely unresponsive meaning I would have to restart with CTRL-ALT-BACKSPACE.

Anyway, I seem to have solved this problem by deleting the file 
/home/USERNAME/.beryl-managerrc

I hope this helps anyone else who has issues with anything similar.

---

