---
title: "qjoypad, anyone?"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Fmac on 2005-11-11
So [Qjoypad]("http://qjoypad.sourceforge.net/") is one of my favourite Linux utilities of all time. My gamepad is my quick launch bar, volume control, and remote control when I watch movies. Or was, now.

The .deb package installed without problem for me on Hoary. The RedHat .rpm installed without problem for me on Fedora Core 4, before that. But now in Breezy, it gives me grief. :(

I get . . .

> fmac@adrastaeia:~$ sudo dpkg --install qjoypad_3.4-1_i386.deb
Selecting previously deselected package qjoypad.
(Reading database ... 101337 files and directories currently installed.)
Unpacking qjoypad (from qjoypad_3.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of qjoypad:
 qjoypad depends on libqt3c102-mt; however:
  Package libqt3c102-mt is not installed.
dpkg: error processing qjoypad (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 qjoypad


So I install every package I can find that's tangentially related to qt3 development, but still no dice, and I try compiling from source, and still no dice.

Has anyone tried getting it working, or got any advice on how I could?

---

### Post by NeoChaosX on 2005-11-11
sudo apt-get install -f

---

### Post by Fmac on 2005-11-11
Update and clarification.

The program is installed, and so far as I can tell, works fine.

The package appears to list a dependency that is deprecated, or perhaps belongs to the main Debian repositories. An Ubuntu package with a different name, presumably, provides whatever qjoypad needs from that package.

So the program does work, but apt-get lists is as Broken, tries to uninstall it at every opportunity, and won't perform other package management operations.

Is there a way to set apt-get permanently to ignore the dependencies for that package? Or would it be simple to rebuild the package without any dependencies listed?

---

### Post by north on 2005-12-19
I think the key here is 
[I]"qjoypad depends on libqt3c102-mt; however:
 Package libqt3c102-mt is not installed."[/I]
Seems like it's looking for a specific qt package which isn't there.  If you installed every package that's related to qt then you might have installed one that actually removed that specific package.  try
**sudo apt-get install libqt3c102-mt** from a terminal window.
Chances are when it hit the dependancy issue it bailed half way through the setup without cleaning up after itself.  Best to remove it and try your
**sudo dkpg -i qjoypad-whatever.deb **again after you've resolved the dependancy stuff.

Update:
I just tried to install that package on my home breezy copy and got the same error.  
sudo apt-get install libqt3c102-mt fixed it. Got some other error about authentication issues when I actually tried to run the program which I haven't looked into yet but qjoypad started up and worked just fine anyway. Cool program.

What do you think?

---

### Post by atf487 on 2005-12-20
Whoa, this is exactly what I'm looking for...if it works with my crappy interact propad6, anyway. Thanks for the link!

---

### Post by zi99y on 2006-01-20
well I had the same problems but had to force depends switch with the dpkg install as the libqt3c102-mt package was outdated, and the newer version with a different name was installed.

So now it works great - love the app, but it doesn't give me an icon in my tray. I know gnome panel is working because other stuff gives the icons. And it still works, if you just click where the icon is supposed to be!

Sorry for vagueness as I'm at work and we don't talk about ubuntu here :confused:

---

### Post by ethana2 on 2007-12-31
I was going to get Nathan(QJoyPad's creator) some updated .deb files, but debcreator is broken-- segfaults immediately.  This is one symptom of a very serious problem; the other is a lack of support for SDL, as far as I can tell.

..created a thread here.  Hopefully we can get these issues properly fixed.
[http://ubuntuforums.org/showthread.php?t=654886](http://ubuntuforums.org/showthread.php?t=654886)

---

