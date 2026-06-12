---
title: "Nautilus crashes when I try to check file properties and gives me a black screen"
date: 2013-07-05
forum: Desktop Environments
---

### Post by Penguenci on 2013-07-05
Hey all you nice people! It's my first post here, and unfortunately it's a help request. The problem occurs only on Unity, so I'm posting in the desktop environments section. Please move it to General Help if appropriate.

Before I start, I'm not a complete noob, but not too far from it. So please bear with me if I seem like an idiot :-)

First off, I'm using Ubuntu 13.04 and it's a fresh install, on a pretty strong computer with healthy components. Ok, so, I've installed quite a few applications and desktop environments, and got myself a bunch of desktop environments and tweaks and what not. Everything was working fine until an hour ago, when I realized right clicking and attempting to check the properties of a file on unity desktop environment crashes my Nautilus. It gives me a black desktop with no icons. Conky remains intact on the right hand side, and I can get the left hand side bar by hovering the mouse over, and restart Nautilus. But whenever I try to check file properties, the problem persists. I tried searching online, but nothing I found was helpful. So here I am posting...

Also, tweak utilities don't run, only gnome tweak tool does, even on Unity. Ubuntu Tweak certainly doesn't launch. I'm not necessarily asking for help for that one on the side, it's just that I find it strange and think it may be related to my problem. In fact it makes me think the issue has to do with the Gnome or Mate installation somehow. I've played around with reinstalling Nautilus too, but to no avail. Another strange thing is that, Gnome Colour Chooser couldn't alter the colour of the start menu despite all my tries. This happened a couple of hours before I realized I couldn't check file properties on Unity. Another thing I did around the same time was removing Gnome Flashback. I did that because I accidentally removed the panels and couldn't get them back in their original form. Played around with that for a while too. Perhaps that's where I messed up? Should I just uninstall everything related to Gnome, or is there any hope of fixing this without taking such a drastic measure?

Please help, I'm totally lost...

---

### Post by stinkeye on 2013-07-05
Have you installed cinnamon desktop from a ppa?
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2152081")

If you installed  other desktops through ppas, may want to look at purging those ppas.
[**_[COLOR="#B22222"]Y PPA Manager[/COLOR]_**]("http://www.webupd8.org/2013/06/y-ppa-manager-099-released-with-support.html") can help you do this.

Gnome Colour Chooser only works with gtk2
Try [**_[COLOR="#B22222"]gtk-theme-config[/COLOR]_**]("http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html")

---

### Post by Penguenci on 2013-07-05
I've installed pretty well anything but Cinnamon, so that's not the problem. But thanks a lot, I'll check those and post my feedback tomorrow. By the way, I just noticed my system settings window has no maximize button while all other windows do. I wonder how I come across all the weirdest problems :-)

---

### Post by Penguenci on 2013-07-05
Alright, I followed your recommendations and the Nautilus crash problem was solved. You're THE man, thank you super much! It was a major annoyance indeed.

But now the login menu has changed into a black one, and I prefer the original. Is there a way to modify that? And it prompts me to log in each time I start Ubuntu. I realize that's not necessarily a bad thing, but I'm wondering if there is a simple way of set Ubuntu to log in automatically at boot again just in case? I couldn't find anything relevant in any tweak manager's menu (which seem to be working now by the way, again, thanks to your method!)

---

### Post by stinkeye on 2013-07-05
> **Penguenci said:**
> Alright, I followed your recommendations and the Nautilus crash problem was solved. You're THE man, thank you super much! It was a major annoyance indeed.

But now the login menu has changed into a black one, and I prefer the original. Is there a way to modify that? And it prompts me to log in each time I start Ubuntu. I realize that's not necessarily a bad thing, but I'm wondering if there is a simple way of set Ubuntu to log in automatically at boot again just in case? I couldn't find anything relevant in any tweak manager's menu (which seem to be working now by the way, again, thanks to your method!)

Not sure what your seeing but see if you can switch to lightdm.
```
sudo dpkg-reconfigure lightdm
```
Use the tab key to move to "ok"

User accounts will allow you to set a user to automatic login.
Type "user" in dash.

---

### Post by Penguenci on 2013-07-07
> **stinkeye said:**
> Not sure what your seeing but see if you can switch to lightdm.
```
sudo dpkg-reconfigure lightdm
```
Use the tab key to move to "ok"

User accounts will allow you to set a user to automatic login.
Type "user" in dash.

Sorry, forgot to post back. Thanks a lot once again, all the trouble is gone! I had already tried the user thing, but the button was greyed out so I thought it wouldn't work. Silly me, it does with a simple click. Just figured that out thanks to your input. 


As for the rest, let me post my experience to serve as reference for other users with the same problem:

```
sudo dpkg-reconfigure lightdm 
```returned ```
package is broken or not fully installed
```

So I did ```
sudo apt-get install -f lightdm
```

which repaired lightdm and now I have my pretty lightdm screen back.

*THREAD SOLVED*

---

