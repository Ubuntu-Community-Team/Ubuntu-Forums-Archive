---
title: "switched desktop from UNR to normal GNOME, now problems..."
date: 2009-07-01
forum: Desktop Environments
---

### Post by mailman1175 on 2009-07-01
I turned on my Acer Aspire One this afternoon to find NO menu bar in the Netbook Remix desktop. I restarted, thinking that might fix it. Still nothing. So I switched to the "classic" ubuntu GNOME desktop, voila! It's there! So I switch back to the "netbook remix". Nothing. Weird. So I switch BACK to the "classic", but no dice.

Isn't Alt-F2 supposed to open a terminal? Either that's not the keystroke combo that does it, or that's not working. I figured I'd need to get a terminal open to troubleshoot... but I got nothin'. It opened up File Manager on the last switch to the "classic" desktop, so I'm going to try to figure out how to open a terminal that way. I did get some kind of error message on the first switch back to the "netbook remix" desktop, and I copied it to clipboard... but lost it somehow.

Something about "an error occurred; some configuration settings may not have been saved".

*shrug*  Help?

---

### Post by mailman1175 on 2009-07-01
OK. The UNR desktop is completely busted. I've managed to open a terminal (by going through the file manager to /usr/bin/gnome-terminal. That's how I had to open Firefox this time. I've tried /usr/bin/desktop-switcher, and it gets me the same results.

In UNR desktop, when I open multiple programs, they stack on top of each other, but you can't switch between them at all... not by clicking on the ones behind, not by Alt-Tab, nothing. I can at least Alt-Tab between windows in the Classic desktop, but the only way I can shutdown is from the terminal.

Whiskey Tango Foxtrot, over? I didn't DO anything, I promise! Grr... This is why I dumped Fedora: It would just show up broke one day, and I'd have to reinstall the OS.

---

### Post by ajgreeny on 2009-07-01
I can't specifically help with your UNR problem as I've never seen or used it, but the keystrokes for the terminal, as you put it, (but it is actually a command line interface, but it amounts to more or less the same thing) is Ctrl+Alt+F1 or F1 - F6 in fact.  Having gone to a cli then Alt+F7 will get you back to the gui without Ctrl.

Alt+F2 gives you the run dialog box normally, but it sounds as if your system is just not doing what it should.  Perhaps a backup from the cli, and reinstall is needed, but I really have no idea about UNR so suggest you wait for more answers.

---

### Post by raymondh on 2009-07-01
Some time ago, there was a BUG about the desktop switcher.  A released .deb file was supposed to have settled the bug.  You may want to check launchpad for updates ... 

[https://bugs.launchpad.net/desktop-switcher/+bug/349519?comments=all](https://bugs.launchpad.net/desktop-switcher/+bug/349519?comments=all)

Good luck.

---

### Post by heine on 2009-07-22
Hi.

I had the exact same problem yesterday and ended up doing a reinstall. Now I don't dare to switch between the UNR desktop and the classic gnome desktop. I'm running UNR on a AA1.

---

### Post by jps1369 on 2009-07-31
I managed to find a fix without having to reinstall.

I was able to find the desktop switcher by:

   Control+F

   click "file system"

   click "search"

   search for "desktop switcher" 

At this point I was able to switch back to the Netbook Remix GUI, but I still had no menu bar at the top of the screen or on open windows. I tried a few things, which only made things worse, then after a bit of googling, I stumbled upon this:

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

I started terminal and entered the command:

   rm -rf .gnome .gnome2 .gconf .gconfd .metacity

logged out, logged in and it was magically working again. 

I may have lost some other settings in the mix, but I hadn't changed much to begin with I expected I might have to fiddle around to get the audio to work, but I didn't have to. Programs are all there, and the few things I did have trouble getting to work in the first place are still working. Hope this helps everyone. Much easier than reinstalling.

---

### Post by coolglobal on 2009-09-10
this bug is still present on netbook remix, GRRRRRRRR!

---

### Post by coolglobal on 2009-09-11
Paste this command in the terminal press enter, then restart, to fix the Ubuntu Netbook Remix Desktop Switcher bug.

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

---

### Post by HarmonicaGoldfish on 2009-10-10
Coolglobal's fix did not work, but the jps1369's fix did.

 When I tried to switch between desktops in Karmic Koala I ended up with a strange hybrid of the two. The only problem with the fix, not really a problem just annoying, is that it reset everything. It erased my favourites, my wireles key...

But at least I have a working desktop back! Guess I won't be switching again.

Thanks


> **jps1369 said:**
> I managed to find a fix without having to reinstall.

I was able to find the desktop switcher by:

   Control+F

   click "file system"

   click "search"

   search for "desktop switcher" 

At this point I was able to switch back to the Netbook Remix GUI, but I still had no menu bar at the top of the screen or on open windows. I tried a few things, which only made things worse, then after a bit of googling, I stumbled upon this:

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

I started terminal and entered the command:

   rm -rf .gnome .gnome2 .gconf .gconfd .metacity

logged out, logged in and it was magically working again. 

I may have lost some other settings in the mix, but I hadn't changed much to begin with I expected I might have to fiddle around to get the audio to work, but I didn't have to. Programs are all there, and the few things I did have trouble getting to work in the first place are still working. Hope this helps everyone. Much easier than reinstalling.

---

