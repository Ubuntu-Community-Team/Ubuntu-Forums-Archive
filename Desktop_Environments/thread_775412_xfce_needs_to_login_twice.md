---
title: "xfce needs to login twice"
date: 2008-04-30
forum: Desktop Environments
---

### Post by DAC1138 on 2008-04-30
I'm running the new Hoary (but I've had this problem even in Gutsy.) Every time I bootup my computer and login via GDM, I choose to have XFCE as my default desktop. I enter my username and password, and XFCE begins loading. After a few seconds, it stops reading files from the hard drive and stops loading alltogether. I have to use CTRL+ALT+Backspace to restart X and re-login to XFCE, where it loads up the XFCE desktop normally. Everything will work fine until I reboot and relogin to XFCE, in which I will have to do the CTRL+ALT+Backspace thing again and re-login.

Here is the error reported in ~/.xsession-errors

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Failed to open the VirtualBox device in the guest.
Failed to connect to the host clipboard.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 10 overrides entry on line 7
Agent pid 5452

---

### Post by DAC1138 on 2008-05-02
Come on, I even provided a logfile! Maybe I should just be vague as hell when I post a problem, that way It'll constantly get bumped to the top of the list and people will have as much information as they need 

Oh yeah...BUMP.

---

### Post by sandrokottos on 2008-05-03
I have the same problem. There is a fix - see here, but it does mean hand editing the xfce desktop file, assuming you're comfortable with that. Works for me

[https://lists.ubuntu.com/archives/xubuntu-devel/2008-April/006176.html](https://lists.ubuntu.com/archives/xubuntu-devel/2008-April/006176.html)

Sandro

---

### Post by DAC1138 on 2008-05-06
Works great. Thanks for the fix.

---

