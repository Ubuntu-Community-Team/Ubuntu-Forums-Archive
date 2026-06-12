---
title: "gnome-theme-manager CPU usage 100% unresponsive"
date: 2007-09-26
forum: Desktop Environments
---

### Post by teknosexual on 2007-09-26
gnome-theme-manager CPU usage 100% unresponsive

Every time I launch gnome-theme-manager, either from Terminal or from the menus, it immediately climbs to 100% CPU usage and becomes impossible to use. It still responds to commands, in that of the 4 themes I can see in the main window, I can click on one and it will reset the theme. However, if I scroll through my list, it just turns to a blur and I can't select a theme. I cannot install new themes either. Basically, if I try to use it, it becomes non-functional.

This is what I received when I launch in Terminal. 
[INDENT]frostbyte@Ironman:~$ gnome-theme-manager
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gnome-theme-manager:11815): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
frostbyte@Ironman:~$ 
[/INDENT]

I am using Feisty Fawn with most recent updates.

I have attached a screenshot of what the Theme Manager looks like when I try to use it and also the System Monitor to show the CPU usage. I also attached 2 more screenshots to show what the Theme Manager looks like when I try to use it.

I can provide more information if you need it but I'm not sure what else to put here. Thanks in advance for any help!

---

### Post by teknosexual on 2007-10-03
Anyone have any ideas? I'm willing to try to anything short of a re-install.

---

### Post by teknosexual on 2007-10-10
Just an update: I have reinstalled **gnome-dekstop** but that didn't help. I have reinstalled anything with the the prefix of "gnome" I could find in synaptic (anything that was already installed that is). 

I've checked the Gnome support forums and bugzilla but I can't seem to find my exact problem.

I also added 2 more screenshots to my original post. I hope that helps.

I really don't know what to do... :(

---

### Post by gaussian on 2007-11-17
> **teknosexual said:**
> Just an update: I have reinstalled **gnome-dekstop** but that didn't help. I have reinstalled anything with the the prefix of "gnome" I could find in synaptic (anything that was already installed that is). 

I've checked the Gnome support forums and bugzilla but I can't seem to find my exact problem.

I also added 2 more screenshots to my original post. I hope that helps.

I really don't know what to do... :(

Did you ever figure out this? This will not probably help you, but I have exactly the same problem with one of my Mandriva desktops (it uses KDE as primary desktop, so it is not a biggie there).

---

### Post by teknosexual on 2007-11-19
> **gaussian said:**
> Did you ever figure out this? This will not probably help you, but I have exactly the same problem with one of my Mandriva desktops (it uses KDE as primary desktop, so it is not a biggie there).

Unfortunately, I still have the problem. No one seems to know a solution.

Perhaps it's not a Gnome or Ubuntu issue then...which is actually more unsettling.

---

### Post by ljpp on 2008-01-07
I don't have the solution either, but yes I reproduced exactly the same issue with my Mandriva 2008 One Gnome.

Also tried Ubuntu Feisty and Gutsy on this but did see an issue like this.

---

### Post by Gigamo on 2008-01-07
I used to have the same issue on my previous install. I installed gtk-chtheme to change themes. After selecting the same theme in both the gnome themes manager and gtk-chtheme, the cpu usage usually was normal.

---

### Post by gaussian on 2008-01-07
As a response to sudden reappearance of activity in this thread I did some new digging. It turned out that my problems in my Mandriva installation were caused by the fact that in my home directory the .gtkrc-2.0 was a symbolic link to a system file that my user did not have writing permissions on. I don't know how that become into being, but removing the link cured the problem.

[B]
Update:[/B] Never mind. It worked couple times, but now the problem has reappeared.

---

### Post by njparton on 2008-01-07
A long shot, but to save a re-installation, try removing compiz from your system and then setting metacity as the default gnome window manager via gconf-editor.

It might be worth a try?

Compiz gave me all sort of problems before I got rid of it.

---

### Post by gaussian on 2008-01-07
Ok, now I finally have figured it out. But whether this works on Ubuntu is uncertain. On my Mandriva installation gnome-appareance-properties (the program that calls what used to be gnome-theme-manager) gets stuck for any user that has the file .gtkrc-2.0 in their home directory. Just removing that file does the trick for me.

Here is a link to an old mandriva bug that made me try this:
[http://qa.mandriva.com/show_bug.cgi?id=9227](http://qa.mandriva.com/show_bug.cgi?id=9227)

---

### Post by teknosexual on 2008-02-10
> **njparton said:**
> A long shot, but to save a re-installation, try removing compiz from your system and then setting metacity as the default gnome window manager via gconf-editor.

Not sure if you were referring to my post, but I do not have Compiz installed on my system.

---

### Post by teknosexual on 2008-02-10
> **gaussian said:**
> Ok, now I finally have figured it out. But whether this works on Ubuntu is uncertain. On my Mandriva installation gnome-appareance-properties (the program that calls what used to be gnome-theme-manager) gets stuck for any user that has the file .gtkrc-2.0 in their home directory. Just removing that file does the trick for me.

Here is a link to an old mandriva bug that made me try this:
[http://qa.mandriva.com/show_bug.cgi?id=9227](http://qa.mandriva.com/show_bug.cgi?id=9227)

Thank you for the tip! I am glad you got that working. I finally got sick of it and did a fresh install Kubuntu.

I will keep your fix in mind if the problem ever pops up for me again in Gnome.

---

