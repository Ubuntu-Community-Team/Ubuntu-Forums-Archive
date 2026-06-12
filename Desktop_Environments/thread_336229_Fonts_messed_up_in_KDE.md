---
title: "Fonts messed up in KDE"
date: 2007-01-11
forum: Desktop Environments
---

### Post by bogdanb on 2007-01-11
Hi! I have a rather weird issue: I noticed today that text *inside* Amarok's window looks very ugly (the window's title-bar is OK). As far as I can tell it's rendered without any hinting.

I use Gnome for pretty much anything, and everything looks OK in the other windows. Amarok is the only thing that is KDE-based, so I assume the setting isn't passed on.

I'm running Feisty. I don't remember seeing this a couple days ago, so I suppose one of the recent updates causes the mess (I do remembers seeing something about fonts being updated), but I don't follow them that close, so I can't tell for sure.

(1) does anyone know a way of looking at the history of updates done by apt-get? I may be able to figure out which package did it.

(2) how do you change font rendering settings for KDE? I'm only familiar with Gnome's menus, and from KDE I have installed only what Amarok requires.

Any ideas where else I can look?

---

### Post by oobuntoo on 2007-01-17
The best way to control the look and feel of KDE apps under gnome is to install kcontrol. Gnome  settings do not have any effect on KDE apps. By installing kcontrol, you can change fonts, font size, style, and color of KDE apps, among other things. After installing, start kcontrol by typing "kcontrol" without quotes on the terminal.

You can check out kde-look.org for kde style that blends in better with the rest of Gnome.

---

### Post by bogdanb on 2007-01-18
I think I need to install more than that. I installed kcontrol, but when I start it (1) I get a couple of errors in the command line:

[INDENT]$ kcontrol 
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
kcontrol: WARNING: No K menu group with X-KDE-BaseGroup=settings found ! Defaulting to Settings/
[/INDENT]

and then the KDE Control Center starts, but it has no setting options. The menu on the left, where I assume the different settings applets should be listed, is empty. Of course, searching for anything (e.g. fonts) also doesn't show anything. I assume I also have to install the KDE analogue to gnome-font-properties. I have no idea what it's called, I'll try searching with Synaptic.

(I tried installing kconfigure, it's the same thing.)

> **oobuntoo said:**
> You can check out kde-look.org for kde style that blends in better with the rest of Gnome.

The theme is OK, I didn't notice any significant difference from the Gnome apps. As far as I can tell, it's just the font rendering that's different (the anti-aliasing method, more exactly).

---

### Post by bogdanb on 2007-01-18
OK, this is really weird. I tried installing qtconfig and qtconfig-q3, they were the only match for "kde font" in Synaptic. There's no option there that controls the font rendering, however, only the actual fonts used.

In the end I gave up and I installed the whole kde-base and kde-core packages. No luck, the kcontrol window still has no applets... I'm stumped.

Another weird thing: the qtconfig window is rendered with correct font hinting. The kcontrol window has the same issues as Amarok, though, and so does Kate. Am I missing some dbus-like component?

---

### Post by Pobega on 2007-01-18
Try installing kde-core and then run kcontrol; If it still doesn't work try booting into KDE and using it.

---

### Post by bogdanb on 2007-01-18
OK, this is getting ridiculous. I did a complete "apt-get install kde", logged-on in KDE, and it still doesn't show anything in the kcontrol window. I'm starting to get pissed...

---

### Post by oobuntoo on 2007-01-18
Have you tried running kcontrol as sudo (root)? If that works, then it's probably some permission-related problem.

---

### Post by bogdanb on 2007-01-18
Yes, I tried that too, it didn't work that way either. (Although the messages in the console got more interesting, it still won't show anything in the window.)

---

### Post by oobuntoo on 2007-02-02
I recently decided to install Ubuntu (Gnome) and installed kcontrol. Yes, it's empty, but found a solution (at least it works for me), thanks to the people at Debian forum. 

command:

sudo mkdir /etc/xdg/menus/kde-applications-merged

sudo cp /etc/xdg/menus/applications-merged/kde-essential.menu /etc/xdg/menus/kde-applications-merged/kde-essential.menu

---

### Post by bogdanb on 2007-02-03
Thanks for your reply. However I couldn't apply your workaround:

[INDENT]
sudo mkdir /etc/xdg/menus/kde-applications-merged
sudo cp /etc/xdg/menus/applications-merged/kde-essential.menu /etc/xdg/menus/kde-applications-merged/kde-essential.menu
[/INDENT]

I don't have the /etc/xdg/menus/applications-merged directory. But I already have the /etc/xdg/menus/kde-applications-merged directory, and it contains a "kde-essential.menu". However that's a directory, not a file as your post suggests it should be. I does contain a same-named file, I'll fiddle with it for a while, but it doesn't seem to contain much. Can you please post the contents of your kde-essential.menu file?

---

### Post by bogdanb on 2007-02-03
OK, I copied the kde-essential.menu file out of it's eponymous directory and now kcontrol really does show its contents. Thanks!

Although, for some reason, the fonts still don't get nice hinting.

---

### Post by oobuntoo on 2007-02-05
This whole kcontrol thing is only to let you know how you can choose font and font size for kde apps. Ugly looking fonts is a different story. There are enough threads on this forum for how to improve that. I don't use the default font setup on my system. I have added the following lines to my sources.list :

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy experimental



This repo is supposed to have improved font rendering libraries. You can check out these links for more details:

[http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)

[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

---

### Post by bogdanb on 2007-02-05
Well, my initial problem was that fonts are rendered ugly *in KDE apps*. The exact same fonts look great in all Gnome apps, so I thought there must be a misconfiguration in KDE. I think both use the same basic libraries for rendering fonts.

I took a look at your links, but they seem to be about Edgy; I suspect the patches are already in Feisty, because the Gnome-rendered fonts are very well hinted and use sub-pixel anti-aliasing. Then again, I think they look just right on my other computer, that has Edgy. I'll look more closely at the links you gave.

---

### Post by bogdanb on 2007-02-05
OK, I looked again and I see one of the threads is about Feisty. I'm reluctant to upgrade to the unofficial version of freetype: I'm not sure if subpixel antialiasing will work correctly after that, due to the patent issues, and things look just great in Gnome right now. I still think it's some kind of Qt issue.

---

### Post by oobuntoo on 2007-02-05
Did you try enabling anti-aliasing and turned on sub-pixel hinting under kcontrol?

---

### Post by bogdanb on 2007-02-05
Yes, of course. I tried all combinations of anti-aliasing, sub-pixel hinting (and all versions of hinting), restarting after each try.

I *think* I did notice a bit of a change after going through all this, but it's still not as good as gnome's hinting.

---

### Post by briguy on 2007-04-04
I'm having the same trouble since I upgraded from Edgy to Feisty.  Everything looks great, except for fonts in KDE apps run as a regular user (running KDE apps as root gets nice fonts).  I did a fresh install of Feisty, but I kept my home directory - I'm assuming that some of the settings from Edgy don't carry well over to Feisty.

---

### Post by bogdanb on 2007-04-05
I guess you could try looking for the file that contains the font settings (root doesn't have any and it works, so if you just remove it you'll probably be fine), but that's going to be hard. KDE stuff is generally in ~/.kde, but I don't know anything more preciese.

Did you manage to install kcontrol? You shouldn't have my trouble, since you've just installed a new Feisty. It has lots of font-rendering-related menus, maybe you can fix things from there.

---

