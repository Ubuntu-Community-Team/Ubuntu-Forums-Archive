---
title: "keyboards shortcut not working after fresh install"
date: 2013-01-01
forum: Desktop Environments
---

### Post by pllX on 2013-01-01
Hello everyone,
I'm trying xubuntu and just did a fresh install on a HP probook laptop.
I noticed some keyboard shortcut are not working :
alt-F5 and alt-F6 do works for horizontal and vertical maximization of windows, 
but alf-F7 and alt-F8 do not.

I'm using a french layout, dont know if it is important
I tried removing .config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml and relogging, but I did not solve the problem...

Where should I start looking to find what's wrong ?

---

### Post by Toz on 2013-01-01
Hello and welcome to the forums.

Looks like theres a little bug there with respect to F7 - there are multiple entries for "maximize_window_key" in ".config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml" 

Since Alt-F10 is the last entry for that action, it (Alt-F10) should work to maximize the window (even though it states Alt+F7). 

A quick workaround is to delete the:```
<property name="&lt;Alt&gt;F10" type="string" value="maximize_window_key"/>
```
...entry from **.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml** _while not logged in_.

As for F8, it seems to work fine for me even on a fresh install. It "sticks" the window to all workspaces so you can see it no matter what workspace you are on.

Note: In Xfce 4.10, you can edit that keyboard shortcut by clicking on the "Edit" button and re-setting it to Alt-F7.

---

### Post by pllX on 2013-01-02
Thanks for answering. You are right !
alt F10 works ! (I did not read the whole .xml file... my bad)
So this means two binding cannot trigger the same thing ? 

You are also right for alt-F8, I works too. I was not understanding the meaning of stcik-windows.

As for xfce version, I'm currently using the 4.8 version which come with xubuntu 12.04
I used apt-cache policy xfce4-utils to know that.
apt-cacge policy xfce4 tells me xfce4 is not installed  (it's a metaPacket, but it should be installed right ?)   and 4.8 is the latest version I can have right now.

---

### Post by Toz on 2013-01-02
> **pllX said:**
> Thanks for answering. You are right !
alt F10 works ! (I did not read the whole .xml file... my bad)
So this means two binding cannot trigger the same thing ?
I don't think so. 

> You are also right for alt-F8, I works too. I was not understanding the meaning of stcik-windows.

As for xfce version, I'm currently using the 4.8 version which come with xubuntu 12.04
I used apt-cache policy xfce4-utils to know that.
apt-cacge policy xfce4 tells me xfce4 is not installed  (it's a metaPacket, but it should be installed right ?)   and 4.8 is the latest version I can have right now.
There is a 4.10 PPA that you can link to so to get Xfce version 4.10 up and running. For more information, see here: [http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html]("http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html")

---

