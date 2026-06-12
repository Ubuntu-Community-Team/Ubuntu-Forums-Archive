---
title: "Going Back to Breezy"
date: 2006-02-27
forum: Desktop Environments
---

### Post by TomAnthony on 2006-02-27
I was wondering if there is any way to revert back to the breezy version of Kubuntu from Dapper Flight 4 and keep my data and installed apps?

---

### Post by TomAnthony on 2006-02-27
I know to upgrade to Dapper you can change the sources.list and change all breezy references to dapper. Can I go back by changing all references to dapper to breezy?

---

### Post by refdoc on 2006-02-27
You will end up in a total mess. 

Why would you want to do this anyway? 

If you are worried about breakage simply cease updating once you have reached a place in Dapper's update cycle where all things work to the way you wish them and wait until Dapper becomes officially stable - next month or so.

Alternatively do it like me - update only when you know you have a day or two to catch up with big problems.

If you *must * revert tyo Breezy, reinstall from scratch.

---

### Post by TomAnthony on 2006-02-27
The latest updates I got for Flight 4 seem to have messed up my display configuration. I can now only get 640x480 resolution. There was an adept error when I was doing the update. I cannot change anything using the display configureation applet. Maybe I will just try another update and see if it fixes it. Any other ideas?

---

### Post by Jedeye on 2006-02-27
try setting up X again

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by TomAnthony on 2006-02-27
Thanks, I will give that a try. I'm a bit new here, but am learning.

---

### Post by TomAnthony on 2006-02-27
And how does the x help the display? ie: what is x?

---

### Post by gingermark on 2006-02-27
From ["What Is the X Window System?"]("http://www.linuxdevcenter.com/pub/a/linux/2005/08/25/whatisXwindow.html"):

The X Window System (commonly referred to as X or X11) is a network-transparent graphical windowing system based on a client/server model. Primarily used on Unix and Unix-like systems such as Linux, versions of X are also available for many other operating systems. Although it was developed in 1984, X is not only still viable but also is in fact the standard environment for Unix windowing systems.

---

### Post by TomAnthony on 2006-02-27
Sweet, lots to read up on. Great help!

---

### Post by TomAnthony on 2006-02-28
[QUOTE=Jedeye]try setting up X again

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

That worked perfectly. Thank you so much!

---

