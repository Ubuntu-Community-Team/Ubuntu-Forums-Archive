---
title: "login/unlock problems after installing thinkfinger"
date: 2008-08-30
forum: Desktop Environments
---

### Post by Temujin_12 on 2008-08-30
I have an IBM Thinkpad Tseries (T61p).  I installed wubi on it and chose kubuntu for the installation.  After installing thinkfinger-tools and libpam-thinkfinger (via apt-get), I have the following problems:


**1.** When I first login from kdm, the screen goes black and I'm dumped to the init screen (showing all the services that have started up).  No errors on the screen and no command prompt. If I login in another session (Ctrl-Alt-F2) and run 'startx' from the command line, kde starts up just fine.


**2.** When I lock the screen (or it locks after going into screen saver), if I type my password (even if I type it over and over) I get the following error:
> 
Cannot unlock the session because the authentication system failed to work. 
You must kill kdesktop_lock (pid {PID#}) manually.
However, if I swipe my finger then type my password it works. But I sometimes have to type in my password a couple of times and click through the error dialog after swiping my finger.

Has anybody ever seen these issues and/or does anyone know how to fix them?  I'd like to avoid having to remove thinkfinger if I can.

Thanks.

---

### Post by sayakb on 2008-08-30
Can you post the output of:
```
cat /etc/pam.d/common-auth
```

---

### Post by Temujin_12 on 2008-08-30
> Can you post the output of```
cat /etc/pam.d/common-auth
```

Yup:
```

auth    sufficient      pam_thinkfinger.so
auth    requisite       pam_unix.so try_first_pass nullok_secure
auth    optional        pam_smbpass.so migrate missingok

```

---

### Post by e04mk on 2008-09-19
If I'm not mistaken, I think I've read somewhere that there's a compatibility problem with login in using thinkfinger in KDE. In gnome, though, it works just fine. Same thing with screen saver. I'll try to find a link to these facts. =)

[https://bugs.kde.org/show_bug.cgi?id=116682](https://bugs.kde.org/show_bug.cgi?id=116682)

---

### Post by chhamilton on 2008-10-03
Yeah, thinkfinger and KDE don't get along too well.  In fact, the problem with kdesktop_lock (the screen-saver locking program) is that it kind of misuses kcheckpass, which does the actual interaction with PAM.  This small utility works with thinkfinger, but only if the calling program uses it properly.

PAM only opens a connection to the fingerprint scanner while a 'PAM conversation' is in place.  Unfortunately, kdesktop_lock gets the password from the user and then feeds it to kcheckpass.  Thus, the PAM conversation is open *after* the password is collected, and any attempt to use the fingerprint scanner is ignored.

To get around this, I've written a small ruby script that replaces kdesktop_lock.  It launches "tf-tool --verify" and the original "kdesktop_lock" simultaneously, and if either of them are successful it unlocks the desktop.

To use this, you need to have ruby installed (sudo apt-get install ruby).  You also need to make sure that all users are able to access the USB fingerprint device.  First, try running "tf-tool --verify" as a normal user.  If this fails with a message "unable to claim USB device", then the permissions are not setup correctly.

First, determine the vendor and product ID by running "lsusb".  Mine outputs something like:

```

Bus 005 Device 005: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

```

The vendor id 0483, and the product id is 2016.  Now, we're going to create a udev rule that gives world read/write permissions to the fingerprint scanner.  Run "sudo vi /etc/udev/rules.d/95-local.rules", and put the following in that file (replace vi with the editor of your choice, and use the appropriate vendor/product ids):

```

BUS=="usb", ATTRS{idVendor}=="0483", ATTRS{idProduct}=="2016", MODE="0666"

```

Now, restart udev with "sudo /etc/init.d/udev restart".  At this point, you should be able to run "tf-tool --verify" without it failing because it can't claim the USB device. (It may fail if you haven't already captured your fingerprint, but I'm assuming you've already done that.)

(You may be tempted to make tf-tool setuid, but this allows people to overwrite other peoples fingerprint files, so this is a bad idea!)

Next, we're going to rename kdesktop_lock with "sudo mv /usr/bin/kdesktop_lock /usr/bin/kdesktop_lock.orig".  Finally, replace it with the included script.  I'm assuming you've downloaded it to your home directory: "sudo cp ~/kdesktop_lock.txt /usr/bin/kdesktop_lock".  We need to make this executable with "sudo chmod +x /usr/bin/kdesktop_lock".

At this point, try running "kdesktop_lock --forcelock" from the command line.  Move the mouse or press a key to bring up the password box, and try swiping your fingerprint.  All should work well.

Unfortunately, KDM doesn't use kcheckpass and it crashes with thinkfinger enabled.  I haven't delved into the code to figure out why, and wrapping it this way like kdesktop_lock isn't feasible.  So, I simply replaced my session manager with GDM.  Less pretty, but it works!

Hopefully this works for you, and hopefully the KDE folks will have a proper fix out sometime soon.  (I'm currently hacking away at kdesktop_lock to see if I can get this working the way it should be.)

Cheers,

Chris

---

### Post by merike on 2008-10-16
Your script seems to work just fine for me on Kubuntu 8.4 :cool:

I guess the script might get overwritten if there are updates to kdesktop package though?

Edit: I guess I got my answer, just day after switching scripts KDE wants to be 3.5.10 instead of 3.5.9. And it does overwrite the script. So keep an eye on updates to kdesktop package ;)

---

