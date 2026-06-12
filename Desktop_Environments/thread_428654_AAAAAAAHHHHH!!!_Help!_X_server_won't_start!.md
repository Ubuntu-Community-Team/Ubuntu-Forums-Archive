---
title: "AAAAAAAHHHHH!!! Help! X server won't start!"
date: 2007-04-30
forum: Desktop Environments
---

### Post by Forlornity on 2007-04-30
Help! When I boot up it says that the X server file has become corrupt and I need to restart!!! Need help!!!
I just did an update and it said summat about not being able to do one, so I did as it said "sudo apt-get install -f" and then restart, now it won't boot, saying the X server is broken! I wan't really paying attention during the whole thing so I can't really answer much about the process involved, anyone able to help?

thanks, Forlornity

---

### Post by taurus on 2007-04-30
Boot into recovery mode from GRUB menu and reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
```
Then reboot and see what happens.

```
shutdown -r now
```

---

### Post by Forlornity on 2007-04-30
thanks, I'll get back to you when I've tried

---

### Post by Forlornity on 2007-04-30
no, it didn't work :( any other ideas?

---

### Post by Forlornity on 2007-04-30
Mcbumped, sorry 'btou this, but I really want my Linux working again! (I'm writing this on Windows)

---

### Post by Forlornity on 2007-05-01
Ok, I have a lot more info now, when I try and boot it says X server c cannot start etc, then it asks if i'd like to see the server output so I say yes, here it is:
```
Stuff About the version and build date etc.


FATAL:Error running install command for nvidia

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found

```

Does that make it any easier to fix?
If it makes any difference, the Version number is 7.1.1, the build date is 07 Jul 06.

thanks, Forlornity

---

### Post by Forlornity on 2007-05-01
Pleeeaaasseeee help meee!
I really want my Linux back!
I'm getting withdrawal symptoms!

---

### Post by taurus on 2007-05-01
If you need to get Linux back, why don't you boot into recovery mode from GRUB menu and replace "nvidia" with "nv" in /etc/X11/xorg.conf?

```
nano -Bw /etc/X11/xorg.conf
```
Save and exit with <Ctrl>o and <Ctrl>x.  Then, reboot and see if X is running again this time.

---

### Post by Forlornity on 2007-05-01
Get back to you when I try...

---

### Post by Forlornity on 2007-05-01
Well that's certainly helped, I'm writing thisun on my linux!
Sorry to be such a noob, but could you explain to me what went wrong or why that fixed it?
Also, any side effects it may have?

thanks, Forlornity

---

### Post by taurus on 2007-05-01
Whatever the nVidia driver you installed, it didn't work well with your graphic card.  By changing the Driver back to nv, you are using the generic nvidia driver--nv--that comes with X.  The only draw back is that nv doesn't support 3D stuff.

What kind of nVidia graphic card do you have anyway?

---

### Post by Forlornity on 2007-05-02
I have a very strange 6645, I think it's just an overclocked 6600 with a bigger number whacked on.
I presume it wouldn't be a good idea to login to my Beryl desktop now then...
Thankfully I only have it as eye candy so no harm done.
Strange thing is, it wasn't until I did some updates that the driver started playing up, could it be that I have an od version of the driver?

---

