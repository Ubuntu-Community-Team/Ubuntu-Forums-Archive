---
title: "Changing default from kdm to gdm"
date: 2005-11-26
forum: Desktop Environments
---

### Post by Stubedoo on 2005-11-26
Hi

I recently installed kde and during the installation process changed my default login screen from gdm to kdm.  Now, when I boot up I get the kubuntu start-up sequence and the kde login window.  This is annoying as I have to select gnome  (which works better for me than kde) from the sessions menu.  Also I can't shut-down / restart directly from gnome, but must first go through the kdm login and then shut-down.  Can someone please tell me how to change the default login screen from kdm back to gdm.

Please note I am fairly new to Linux.

Cheers

---

### Post by Xian on 2005-11-26
Open a terminal and issue this command:

```
$ sudo dpkg-reconfigure gdm
```

---

### Post by metoo on 2005-11-26
That should not happen with KDM!

KDM 'remembers' your last session and will boot into it as default.

Can't say anything to the extra step on shut down. This is not required in KDE but might be in gnome as you say.
Sure, that you selected the shut down command on exit in gnome?

---

### Post by atoponce on 2005-11-26
You can use Gnome by default using the kdm and vise versa using KDE with the gdm.  Just set it to the default when asked.  It wil boot into the window manager of your choice, regardless of the desktop manager you are using.

The only drawback, as you have noticed, is when you are using a window manager different from the desktop manager, you do not have direct access to rebooting and shutting down- only logging off.  Shutdown and reboot are handled by the desktop manager, and as such, you have to log off first then take the extra step to shutdown or reboot.

If you are using the same window manager with the desktop manager (gdm with Gnome, kdm with KDE), then this extra step isn't needed.

The only exception to this rule, that I have found, is when using XFCE.  Even though your desktop manager may be gdm or kdm, when you boot into XFCE, you have direct access to reboot and shutdown as well as logging off.

HTH

---

### Post by Stubedoo on 2005-11-26
Thanks for the help - it starts up with gdm now.  The only problem the start-up sequence (before the login screen) continues to say Kubutu rather than Ubuntu, but I think I can live with that.

By the way, as I never tried logging on without first selecting gnome, I didn't realise that KDM starts with your last session type (i.e. Gnome or KDE).


Cheers

---

### Post by Xian on 2005-11-26
[QUOTE=Stubedoo]Thanks for the help - it starts up with gdm now.  The only problem the start-up sequence (before the login screen) continues to say Kubutu rather than Ubuntu, but I think I can live with that.[/QUOTE]

Issue the command below from a terminal.
The output from my box has been provided.

```
$ sudo update-alternatives --config usplash-artwork.so

There are 2 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/lib/usplash/usplash-default.so
*+    2        /usr/lib/usplash/kubuntu-splash.so

Press enter to keep the default[*], or type selection number:
```

---

### Post by abbeychase on 2006-11-13
is it possible that someone can just let us know what the directory and conf file is that says to load gdm or kdm so that one could go in an change the default manually?  These are where most of my issues reside is not knowing where ubuntu puts things.

---

### Post by evil_cat on 2008-05-11
this solution works perfectly fine for me

you can also try 

sudo apt-get remove kubuntu-desktop
sudo apt-get remove ubuntu-desktop

---

