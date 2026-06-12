---
title: "Problem after trying ubuntu without installing?"
date: 2009-02-15
forum: General Help
---

### Post by thegreattacoman on 2009-02-15
So I was curious about ubuntu, so last night I tried it out straight from the CD without installing it, just so I could see what it was like.  Well I took out the CD and when I restarted my computer it still went back to the "Choose operating system" screen where it asked me if I wanted to load up XP or Ubuntu.  Just to see what would happen I chose Ubuntu and it just gets stuck at the loading screen before Ubuntu loads up.  It just looks like it keeps loading.  So I just wanted to know if anybody could help me get rid of that original booting screen and just have it go to XP normally.  I might dual boot Ubuntu later, but I want to make sure there's not going to be anything to screw it up somehow.

NOTE: This may be the source of the problem, but I'm unsure.  I was fooling around with the desktop settings, and I tried turning on effects, and it started loading this driver but I couldn't cancel out of it for some reason, so the bar got to 100%.

Any help would be greatly appreciated, thanks.

---

### Post by Altay_H on 2009-02-15
That menu is probably a program known as GRUB. The easiest way to remove it is to use a utility called Super Grub.

Download the CD image from this link: [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Burn it to a CD and boot into it the same way you would Ubuntu. There should be an option to restore Windows from within Super Grub. That should remove GRUB for you.

---

### Post by thegreattacoman on 2009-02-15
Thanks for the response.  I don't have a blank cd at the moment, but I'll post the results after I get one and go with your suggestion.

---

### Post by Altay_H on 2009-02-16
If you have the Windows XP CD you should be able to solve the problem [this way]("http://www.blogmanno.com/?q=node/9"):

[QUOTE=www.blogmanno.com]In Windows XP, you can uninstall GRUB as follows:

Boot from the Windows XP CD and press the "R" key during the setup in order to start the Recovery Console. Select your Windows XP installation from the list and enter the administrator password. At the input prompt, enter the command "FIXMBR" and confirm the query with "y". The MBR will be rewritten and GRUB will be uninstalled. Press "exit" to reboot the computer.[/QUOTE]

---

### Post by thegreattacoman on 2009-02-20
Alright so I solved the problem.  There was something I forgot to mention.  When I tried Ubuntu without installing it, I wanted to run it off the CD, but for some reason Windows didn't want to boot the CD.  So I loaded up the CD while in Windows and there was an option to "Help me Load Up CD" or something like that.  I chose that and as it turns out, it installed Wubi on my system.  Looking through some files today, I uninstalled it and everything is back to normal.  Thanks for the responses though, I appreciate it.

---

