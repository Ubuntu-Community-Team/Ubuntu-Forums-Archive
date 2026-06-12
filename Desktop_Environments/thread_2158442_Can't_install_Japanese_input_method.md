---
title: "Can't install Japanese input method"
date: 2013-06-29
forum: Desktop Environments
---

### Post by berndbausch on 2013-06-29
This is Lubuntu 12.10 on an old IBM Thinkpad R31, 384MB memory and Celeron CPU, freshly installed from CD, though I did a *get-apt update* right after logging on for the first time.

I need Japanese input (I am fine with English menus, error messages etc). Under *Preferences->Keyboard Input Methods*, tab *Input Method*, the list of imput methods is empty. The *Add* button is grey and can't be clicked.

Under *Preferences->Language Support*, I can click *Install/Remove Languages*. This however brings up a window with an error message:

[INDENT]**Could not install the full language support** org.freedesktop.DBus.Error.NoReply: Didi not receive a reply .....(snip).....[/INDENT]

After this, the keyboard input method configuration tool has not changed.

Earlier, I tried to remedy this by upgrading to the latest version of Lubuntu. This left me with a black screen after reboot, so that I am not too eager to do this again.

[I][B]Does anybody know where the reply mentioned in the error message is supposed to come from?
What is the manual way (command line) to install and configure a Japanese input method?[/B][/I]

Thanks,

Bernd Bausch, Tokyo

---

### Post by Rex Bouwense on 2013-06-29
Welcome to the Ubuntu forums.  I too am using Lubuntu (12.04, 12.10, and the newest 13.04).  I have checked on each version and I could have (if I want to do so) installed the Japanese language pack in each one.
This site
[http://lxlinux.com/#18](http://lxlinux.com/#18)
tells you how to set your computer up to be able to change from one keyboard to another, but that does not seem to be your problem.  Out of pure curiosity why didn't you select Japanese when you installed?
I also found
[http://ubuntuforums.org/showthread.php?t=1899161](http://ubuntuforums.org/showthread.php?t=1899161)
[http://ubuntuforums.org/showthread.php?t=1595258](http://ubuntuforums.org/showthread.php?t=1595258)
They may be a bit dated.

---

### Post by Irihapeti on 2013-06-29
The OP's computer is rather light on memory.

I don't know if Lubuntu uses iBus or SCIM. If it's iBus, it might be worth changing to SCIM, which seems to work reasonably well on lower-memory systems. You'd probably have to use "legacy" input methods, though.

It might also be that although the basic input engine is there and working, there are no specific input methods installed. They'd need to be installed via apt-get or other package installer.

---

### Post by berndbausch on 2013-06-29
Rex, many thanks. I didn't set up Japanese as the main language since I am fairly computer-literate but not that fluent in Japanese. But it's probably easier to add English as the second language after installation, so this is a great suggestion.

The LXDE documentation you mention looks very interesting.

Finally, I will also look into SCIM as the next poster suggested. Again thanks much for your inputs.

---

