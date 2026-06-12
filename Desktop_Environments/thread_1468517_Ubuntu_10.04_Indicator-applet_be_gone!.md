---
title: "Ubuntu 10.04 Indicator-applet be gone!"
date: 2010-05-01
forum: Desktop Environments
---

### Post by CptSkippy on 2010-05-01
I hate the indicator applet, how do I correctly get rid of it?  

I removed it in the package manager and now I get two lovely errors at login.  I suspect that these are a result of the applets not being removed from the panel before I removed their packages but in NBR someone decided to lock the panel!?

> The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

The panel encountered a problem while loading "OAFIID:GNOME_IndicatorApplet".

I really resent that this applet is forced upon users of NBR without any configuration options at all or a way to opt out of it.

---

### Post by Chargerbear on 2010-05-09
Maybe you wont have to worry about it. It just crashed on my desktop 10.04 AMD64 installation and is asking me if I want to delete it. That's how I found your post. I didn't know if I wanted to delete it or not 'cause I didn't know what it was. After reading your post I decided I will probably be better off if I didn't know what it is and say yes to deleting it. I know this doesn't help you with your problem, but thank you for solving mine.:) Thanks Again Chargerbear

---

### Post by wowshailen on 2010-07-14
I really hate it too Ubuntu forces one to use things it wants. There is no way to just disable the indicator-applet/remove it.

If I try to remove it from Synaptic, it attemps to remove ubuntu-launcher, the nice interface on the desktop.

Another bad things about Ubuntu 10.04 Netbook remix is that there are no ways I can modify what I want to see in the desktop panels (I'm talking about the nice netbook interface to choose apps.)

One can modify what apps one can see using Menu editor, but I cannot add my custom program, or remove a particular folder from the 'Files & Folders' tab.

Very bad for an open source software.

---

### Post by stephan_1n on 2010-07-16
I have the same error with my 9.04 :

The panel encountered a problem while loading "OAFIID:GNOME_NotificationAreaApplet".
The panel encountered a problem while loading "OAFIID:GNOME_IndicatorApplet".
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".
The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".
The panel encountered a problem while loading "OAFIID:GNOME_WorkspaceSwitcherApplet".
The panel encountered a problem while loading "OAFIID:GNOME_WindowListApplet".
The panel encountered a problem while loading "OAFIID:GNOME_ShowDesktopApplet".
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

is there some shell scripts to run to fix all this ? some thing like "sudo apt-get blablabla install"

---

