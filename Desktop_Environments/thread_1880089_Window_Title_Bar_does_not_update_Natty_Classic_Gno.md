---
title: "Window Title Bar does not update Natty Classic Gnome Multiple Monitors Virtual Box"
date: 2011-11-12
forum: Desktop Environments
---

### Post by JustinGordon on 2011-11-12
I've been struggling to get my newish HP Pavilion dv7 laptop behaving well using VirtualBox and Ubuntu Natty. I figured out that if I log into Natty using classic gnome, screen updates are MUCH happier and I can even run dual monitors almost perfectly. It's so much better than unity! And the other compiz settings are the ones I really like. It's almost super awesome.

However, there's still ONE thing that is bugging me like crazy. The window title bar never updates unless one switches from maximized to not maximized and vice-versa. I have not seen any other report of this problem. Where in the world could the setting or work-around be so that window title change are correctly reflected by the window decorator. I've tried both the default compiz-decorator and the gtk-decorator. I noticed that on native natty install, the window title updates after a small lag.

What could it be about running under virtualbox or gnome that is causing the decorator to fail to update the window title.

Any advice would be greatly appreciated.

Thanks,

Justin

---

### Post by JustinGordon on 2011-11-14
More observations:
1. The title bar does not change color to show the window got focus.
2. Resizing the window in any way makes the title bar text to update.

Any advice? Thanks in advance.

Justin

---

### Post by JustinGordon on 2011-11-14
I just verified that if I use Ubuntu Classic No Effects,then the window highlight, naming works correctly. However, I saw other drawing problems in that mode, so I'm not going back to it.

So this seems to be a problem with the window decorator.

I'm running dual screens on Virtual Box (windows 7 host), Natty 11.04.

Thanks,

Justin

---

### Post by Deltik on 2011-11-15
I had this issue.  It was one of the many reasons why I switched back to Ubuntu 10.04 Lucid Lynx.  By the way, I added your window title bar bug to [my report]("http://ubuntuforums.org/showthread.php?p=11353243"), JustinGordon.

In the past day, I found something called [MATE Desktop Environment]("http://matsusoft.com.ar/projects/mate/"), a fork of the classic GNOME 2.  The developer doesn't seem know English well, but [Linux Mint picked it up]("http://www.linuxmint.com/rel_lisa_whatsnew.php") and is working on it.

Linux Mint 12 "Lisa" is shipping with MATE, and according to [some sources]("http://www.ubuntubuzz.com/2011/11/install-linux-mint-12-application-in.html"), it's compatible with Ubuntu 11.10.

Here are the instructions to install Mint MATE on Ubuntu 11.10.  (I've tested the instructions up to installation, but I haven't actually used MATE before.)

[LIST=1]
[*]Load *Software Sources*.  This can be accessed by searching the dash or opening it from Ubuntu Software Center.
[*]Change to the tab "Other Software".
[*]Click "Add...".
[*]Add this APT line:
```
deb http://packages.linuxmint.com/ lisa main upstream import
```
[*]Try to close out of *Software Sources*.  You should get a dialog box with the bold text, "**The information about available software is out-of-date**".  Do not click "Reload".  Click "Close" instead.  If you have already clicked "Reload", do not panic about the error and skip step #7.
[*]Open a *Terminal*.  This can be accessed by searching the dash.
[*]Run this command:
```
sudo apt-get update
```
[*]Run this command:
```
sudo apt-get install linuxmint-keyring
```
[*]This is the command to install Mint MATE:
```
sudo apt-get install mint-meta-mate
```
[*]*(I have not tested this step.)* Log off and log on using "lightDM".
[/LIST]

---

### Post by JustinGordon on 2011-11-16
Argh...Discovered a new issue with my Natty virtualbox setup, using classic gnome with compiz.

The Evernote Chrome extension to clip an article totally locks up the windowing graphics system. At first Chrome locks up, then all the windows go blank. It's probably something to do with the masking of the window to pick the article section.

I can still reboot gong to tty1, but that's about it.

This is reproduce-able every time.

---

### Post by Daniel15 on 2011-11-18
> **JustinGordon said:**
> However, there's still ONE thing that is bugging me like crazy. The window title bar never updates unless one switches from maximized to not maximized and vice-versa.
Sounds like the same issue I'm encountering. Are you using the ATI "fglrx" driver by any chance? If so, this is probably [bug 770283](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/770283). Click the "Does this bug affect you?" and choose "Yes" so that the developers know how many people this bug affects.

---

