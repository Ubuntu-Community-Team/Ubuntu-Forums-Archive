---
title: "Intermittent Nautilus Crashes (Edgy)"
date: 2006-11-07
forum: Desktop Environments
---

### Post by kungfoofool on 2006-11-07
I don't know where else to go for this, because it's a vague problem that only happens inconsistently. If I click the "Trash" icon in gnome, or click on a folder on the desktop, sometimes Nautilus crashes. The icons on the desktop disappear and I have to run "killall nautilus" and restart nautilus for the problem to be resolved.

Am I the only one having a problem with this? I'm running a fresh Edgy install.

---

### Post by justinjstark on 2006-11-07
Nautilus has been flaky in this release of gnome.  I sometimes find that video thumbnailing (using totem-video-thumbnailer) causes nautilus to crash/freeze (especially in a directory with a vid currently downloading).  Once it's closed I often have to killall nautilus before it will open again.  It doesn't happen too often so I can live with it.  Let's just hope this gets ironed out in feisty fawn / gnome 2.18.

---

### Post by zgornel on 2006-11-08
Yes, nautilus keeps crashing in Edgy. Hope there will be some update to fix this ...

---

### Post by kungfoofool on 2006-11-08
> **zgornel said:**
> Yes, nautilus keeps crashing in Edgy. Hope there will be some update to fix this ...

Amen to that. It's starting to get a little irritating.

---

### Post by altonbr on 2006-11-13
I figured it was because of Azureus, but I think it was happening before I installed that through Automatix2 (just wanted to test it out).

And I didn't know the commands before, I always had to restart the computer :S. I'm such newbie.

```
$ killall nautilus
$ restart nautilus
```

Thank you for the tips!

---

### Post by justinjstark on 2006-11-13
> **altonbr said:**
> I figured it was because of Azureus, but I think it was happening before I installed that through Automatix2 (just wanted to test it out).

And I didn't know the commands before, I always had to restart the computer :S. I'm such newbie.

```
$ killall nautilus
$ restart nautilus
```

Thank you for the tips!

Actually restart is not a command.  Just "killall nautilus" and then reload the file browser from the menu or type "nautilus" from the console.

---

### Post by Makurosu on 2006-11-14
It's more than just Nautilus for me.  When Nautilus crashes, I'm also unable to open a terminal.  Anybody else get that?  Nautilus and Terminal each act like they're starting up for a moment, but then they never do.  I'd love to be able to open a terminal and say "killall Nautilus" if that really works.  I've tried ending all the Nautilus processes in System Monitor, but that doesn't help either.  I can reboot and that will solve the problem until next time, but I'm typically working on my home computer remotely from work and there is another bug (#65795) where the password in vino gets reset after a reboot, and then I'm unable to log in remotely again until I set the Remote Desktop password again locally.  Argh.

I really hope all these bugs get fixed at some point.

---

### Post by justinjstark on 2006-11-14
> **Makurosu said:**
> It's more than just Nautilus for me.  When Nautilus crashes, I'm also unable to open a terminal.  Anybody else get that?  Nautilus and Terminal each act like they're starting up for a moment, but then they never do.  I'd love to be able to open a terminal and say "killall Nautilus" if that really works.  I've tried ending all the Nautilus processes in System Monitor, but that doesn't help either.  I can reboot and that will solve the problem until next time, but I'm typically working on my home computer remotely from work and there is another bug (#65795) where the password in vino gets reset after a reboot, and then I'm unable to log in remotely again until I set the Remote Desktop password again locally.  Argh.

I really hope all these bugs get fixed at some point.

A few tips:

You could try pressing alt+f2 and issuing "killall nautilus" from the run field.  Or another alternative is to ctrl+alt+f1 to get to a terminal screen, login in and killall nautilus from there, and the ctrl+alt+f7 to get back to gnome.

You should never have to restart linux unless you change something at the kernel level.

---

### Post by Makurosu on 2006-11-14
> **blaksaga said:**
> A few tips:

You could try pressing alt+f2 and issuing "killall nautilus" from the run field.  Or another alternative is to ctrl+alt+f1 to get to a terminal screen, login in and killall nautilus from there, and the ctrl+alt+f7 to get back to gnome.

You should never have to restart linux unless you change something at the kernel level.

Thanks for the tips.  Issuing "killall nautilus" in the run field didn't solve the problem.  Even when I checked "Run in terminal."  The terminal window never opened.  Also, nothing happened if I ran "nautilus" or "gnome-terminal" from the run field.  Something is apparently screwed up, but the problem always goes away after a reboot.  At least until the next time it happens.  So, I'm not sure what else to do.  I wish I could reproduce the steps it takes to get into this error condition.  It seems to happen randomly.

---

### Post by vificunero on 2006-11-15
I have problems with Nautilus too: when I need a window and I click on the icon it just opens ten and more windows and all I can do is to kill it.

---

### Post by BrandonObrien on 2006-11-16
The same thing just started happening to me this morning.

I woke up and went to my computer.  I had Gaim open and was about to type a message and gaim dissapeared.  I then went to the Applications menu to re-launch Gaim and the menu and my desktop icons dissapeared.

I had a terminal window open and tried killall nautilus but it said bash: killalll not recognized (or soemthing to that effect).

I tried relaunching nautilus and that didn't do anything either.

Hitting Alt+F2 didn't bring up the search box either.


i have no idea what's going on.

---

### Post by crendon on 2006-11-25
Humm I have noticed all same problems as you guys. Sometimes without reason nautius crash... (machine idle). Somethimes it freezes and even I cant even access to terminal (never login). Anyway lest wait for the patches.

---

### Post by leftcase on 2006-12-03
Try reinstalling nautilus...

```
sudo apt-get remove nautilus
sudo apt-get install nautilus
```

Nautilus crashed every time gnome started after I did a clean install of Edgy. Removing nautilus then installing it again got it up and working.

I'm not sure if the issue could possibly related to a corrupted install....

---

