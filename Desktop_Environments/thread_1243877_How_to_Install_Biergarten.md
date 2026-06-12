---
title: "How to Install Biergarten"
date: 2009-08-18
forum: Desktop Environments
---

### Post by Tums:) on 2009-08-18
**[SIZE="5"]Biergarten Install Help Needed!!![/SIZE]**

I am trying to install a new desktop theme named Biergarten and I need help!  I downloaded the .zip file and it includes Emerald, tar.gz, and GTK2.0 components.  I found some instructions to install Emerald themes but the only thing that changes is the window title bar.  I also tried dragging the tar.gz files into the "Appearances", "Themes" window; but no success.  Does anybody know what steps I need to take to install this theme?  I am running Ubuntu 9.04 and have a ATI Raeon X1200 graphics card.  Oh, also its the AMD64 bit version of Ubuntu.

Would someone please help me?

---

### Post by Kevanx on 2009-11-01
I'd be happy to help, although I'm not sure I can help you with all of it.

There are basically three tools that are vital to this theme.

1. Emerald (which you seem to have under control)
2. Conky (which I have never used), which creates the desktop clock its appearance.
3. Avant Window Navigator - which gives the launcher.

I haven't used Conky, but I believe he shares his configuration file in the zip file, which should make things fairly easy.

As for AWN (Avant Window Navigator), install it, using: ```
sudo apt-get install avant-window-navigator
```

Then you just need to configure it. Put the icons in a memorable location like /home/YOUR_NAME/.icons/biergarten then right-click on the launchers that you've added, and choose "Change Icon" and point to the icon as you like it. Right-click again, Choose "Dock Preferences". Then fiddle! you'll want to change the colour and opacity of the "Glass Engine" and put the "Look" as "Flat Bar".

Then, [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=1026971") will tell you how to get the width at 100%, so that it looks exactly as his does, but I like mine with colorful icons, tucked away on the left hand side.

As for Conky, there are bound to be plenty of readmes about it, but my desktop is almost never visible anyway, so I'm good with having the time in the menubar, and on my wrist.

Hope this helps!

---

