---
title: "about 'reboot'"
date: 2008-01-24
forum: Desktop Environments
---

### Post by JediKnight on 2008-01-24
I was experimenting with xorg.conf trying several options and drivers. The question is: do I have to reboot each time I make a change? The boot time is very long, so how can I reset X?

Is ctrl-alt-backspace enough, or do I need some rmmod as well?

---

### Post by erginemr on 2008-01-24
rmmod (and more appropriately modprobe) is used for something else, to add/remove modules from the Linux kernel. If I were you, I whould stay away from them unless you know what you are doing. Besides, AFAIK, it should have nothing to do with graphical settings, unless you are messing with NVIDIA, etc. kernel modules.

A simple Ctrl+Alt+BackSpace should restart your X server just as you have indicated.

---

### Post by JediKnight on 2008-01-24
Thanks for the reply!!

However how do you explain this?

> Note: An alternative to rebooting is to restart the X Server by pressing your CTRL ALT BACKSPACE keys. You must remove any old kernel modules such as "drm" "radeon" or "fglrx" using the "rmmod" command. Example: sudo rmmod fglrx

Foud in [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by erginemr on 2008-01-24
As I said, the passage you have quoted apparently deals with the installation / removal of ATI drivers (radeon, fglrx) and is a specific post installation step. You don't have to rmmod modules everytime you make changes to xorg.conf such as playing with screen resolutions, etc. The question is, what changes do you often make in your xorg.conf file? Are you trying to install the ATI driver?

---

### Post by JediKnight on 2008-01-24
Yes, please have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=676807") if you don't mind

---

### Post by erginemr on 2008-01-24
Can you please post your whole "/etc/X11/xorg.conf" file here? Maybe not me, but someone else can perhaps make something out of it...

And one more question, did you disable the ATI kernel with DISABLED_MODULES="fglrx"?

EDIT: Also please check out the following official howto as well, if you haven't done already:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by JediKnight on 2008-01-26
Oh another issue: about 50% times I relogon with ctrl-alt-back, some warning wondows show up > 'The panel encountered a problem while loading "OAFIID:GNOME_blah blah" and then prompts to delete the applet (???) or not

Some applets that have this problem are Fastuserswitchapplet, Mixerapplet etc

Even if i press don't delete, they won't show up in the panel

---

### Post by erginemr on 2008-01-26
Oh, that is probably an overall bug in Gnome applets, occuring to me as well. There is a thread and a bug report dedicated to this problem:
[http://ubuntuforums.org/showthread.php?t=608767](http://ubuntuforums.org/showthread.php?t=608767)
[https://bugs.launchpad.net/ubuntu/+bug/164804](https://bugs.launchpad.net/ubuntu/+bug/164804)

One possible cause may be the leftovers in your /tmp folder from your latest session, as a result of a sudden death by Ctrl+Alt+BackSpace. We have been circumventing this problem by deleting what is inside the /tmp folder and some people opted for an uninstallation followed by a reinstallation of the Gnome applets. But the problem still haunts Gutsy users from time to time.

---

### Post by gamathers on 2008-02-09
> **erginemr said:**
> Oh, that is probably an overall bug in Gnome applets, occuring to me as well. There is a thread and a bug report dedicated to this problem:
[http://ubuntuforums.org/showthread.php?t=608767](http://ubuntuforums.org/showthread.php?t=608767)
[https://bugs.launchpad.net/ubuntu/+bug/164804](https://bugs.launchpad.net/ubuntu/+bug/164804)

One possible cause may be the leftovers in your /tmp folder from your latest session, as a result of a sudden death by Ctrl+Alt+BackSpace. We have been circumventing this problem by deleting what is inside the /tmp folder and some people opted for an uninstallation followed by a reinstallation of the Gnome applets. But the problem still haunts Gutsy users from time to time.
I am having the same problem, but I'm loading 7.10 from scratch. I assume this applet is not needed to continue the loading process?

---

### Post by salviablue on 2008-03-01
I am also having the same problem with "The panel encountered a problem while loading OAFIID: blah blah" but only during either logging out and logging back in (either as a different user or the same user) or/and ctrl+alt+backspace. I get about 7 of these. The only way to not get these is to reboot the whole thing, not just X.
  This is getting embarrasing, after defending my decision to do the total switch to Ubuntu from Window$ to some friends and being able to `fire back` with problems I dont have that they do, this prob always seems to happen when they are round and watching!
  I dont seem to be able to find these applets to restart them. I was thinking i could just write a simple script reload the offending applets. Any words from the wise??PLEASE??

---

