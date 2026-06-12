---
title: "dell mini 9 w/ 9.04 recently installed"
date: 2009-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Brianc0713 on 2009-05-27
after installing 9.04 from a usbdrive and installing updates. i now have no panels... what should i do? i can right click and options show up but i cannot run anything.

---

### Post by KegHead on 2009-05-27
Hi!

I can't help you, but my 9.04 clean installation was flawless.

I'm curious to hear from the group what might have happened.

KegHead

---

### Post by ugm6hr on 2009-05-27
Did you install the Netbook Remix or the standard desktop Ubuntu (or possibly Xubuntu, or used XFCE+NBR)?

Was the desktop correct to start with?

Have you enabled any unusual repositories?

My panel misbehaves occasionally (see my post elsewhere), but the Gnome panels don't generally disappear.

---

### Post by Vaun on 2009-05-27
Press Ctrl+Alt+F1 to gain access to a text console (your screen will turn black with a prompt in white text, and if not running from the CD you may be asked to login).

```
sudo rm -rf ~/.gconf .gconfd .gnome2
```

Press Ctrl+Alt+F7 (to return to the graphical interface). 

Restart X by logging out and back in, or typing sudo /etc/init.d/gdm restart. 

You're settings are going to be restored to the default ones.  This seems to be an issue with the desktop-switcher.

I built the new settings for ume-config-netbook from bazaar trunk and that did seem to reconcile issues.

I am using the default GNOME desktop without the bottom panel and the winoow-picker applet.  This makes very good use of the real estate on my Dell Vostro A90 and allows me to use Compiz.  Compiz and the netbook-launcher are not playing well together at the moment.

---

