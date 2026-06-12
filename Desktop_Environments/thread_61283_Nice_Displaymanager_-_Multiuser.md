---
title: "Nice Displaymanager - Multiuser"
date: 2005-08-31
forum: Desktop Environments
---

### Post by daller on 2005-08-31
Hi All,

In Kubuntu, I really miss a multiuser displaymanager!

Is there a nice one, and how do I install it?

Cheers, Daniel

---

### Post by incinerator on 2005-08-31
Please specify what exactly you mean a "Display Manager" to be.

kdm and gdm are sufficient display managers, and they support multiple users, too.

In the X-Windows world, as display manager is the preferred term for the program that basically puts the login-screen onto the display. If you installed kubuntu, you will see kdm. If you installed ubuntu, you will see gdm. Both variants support multiple users, just like any other login-screen. They also support multiple desktop environments, if set up properly. E.g. you can use kdm to log into a non-kde (e.g. gnome) desktop session and vice versa. Afaik, for ubuntu, most desktop environments should be supported out-of-the box as soon as they get installed.

---

### Post by daller on 2005-08-31
Well, sorry...

I have KDM installed, but only with the standard theme!

What I want, is to have a theme where all users are shown, so that any users of the computer, doesn't have to type in the username (Just click an icon)

..."good" old Windows XP style!

---

### Post by incinerator on 2005-08-31
Well, the default kdm supports this and it is easy to configure it using kde "login manager" module of the kde control center. See [here](http://kudos.berlios.de/kf/kisimlar/useradmin.html#otologin) to find out where that thing is.

However, I only know this to work with a pristine kde. Kubuntu's kdm looks quite a bit different from the pristine one, changing options in the kontrol center might not work.

---

### Post by daller on 2005-08-31
Well, tried to edit the data, but as you mentioned - The changes doesn't affect KDM...

How do I make it work?

---

### Post by incinerator on 2005-08-31
1. Make sure you run the "Desktop Manager" kde control centre modul in system administrator mode.

2. Simply logging out of kde probably won't do it, you may have to restart kdm:
sudo /etc/init.d/kdm restart

---

### Post by daller on 2005-09-01
I logged into administrator-mode, but where do I change the theme?

---

