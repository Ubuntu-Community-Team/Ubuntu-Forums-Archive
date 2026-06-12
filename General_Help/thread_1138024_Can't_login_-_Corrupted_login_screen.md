---
title: "Can't login - Corrupted login screen"
date: 2009-04-26
forum: General Help
---

### Post by argonaut747 on 2009-04-26
Hi all.
LOVE Ubuntu.
I've been using it for a couple of months now and it's great fun with some fantasic software. But that's the praise now on to the problem.
I upgraded to 9.4 the other day. When using 8.10 every now and then the login screen was corrupted. I reset and all was well.
I have an ati 9600 graphics card.
My session type is GNOME.
AMD 2600+
1.5 Gig RAM
110 Gig Hard Drive.
Last night I activated the ati driver and it downloaded and I restarted. Now I get the corruption :-(.
I thought I may be able to login so I entered my password and nothing happens.
The numlock key doesn't work so I assume the system is locked.
I don't mind reinstalling as I use the system just to play with Linux at the moment but I'd rather fix it than just re-install.
Any suggestion would be appreciated.
Take care and thank you in advance.

---

### Post by Legace on 2009-04-26
Here you go:

> **gocek said:**
> BTW: if you fail to boot up your Ubuntu, just reboot it, select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

