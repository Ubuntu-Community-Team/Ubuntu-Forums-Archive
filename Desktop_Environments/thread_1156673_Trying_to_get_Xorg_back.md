---
title: "Trying to get Xorg back"
date: 2009-05-12
forum: Desktop Environments
---

### Post by guedesav on 2009-05-12
I've tried to include a function in my xf86Xinput headers by manually installing a newer version of XFree86, bit it didn't work, but as a consequence my system has automatically changed the X Server from X.org to XFree86, and XFree86 is doing some damage to my previous configuration(mainly, my keyboard, which can't input a non-numpad / anymore, let alone question marks...).

Long story short, what is the conf file I need to alter to get my sistem back to xserver-xorg?

PS.: Yes, I had to cut-paste that question mark. Please help ASAP.

---

### Post by andrea000 on 2009-05-12
Type any one of the following command to reconfigure X.org 
windows system

As the root user

dpkg-reconfigure xserver-xorg

OR as a normal user

sudo dpkg-reconfigure xserver-xorg

Just follow on screen questions and you should able to 
restore or reconfigure to previous state.

---

### Post by guedesav on 2009-05-12
Nuh. Tried that first of all. XFree86 stays.

---

### Post by andrea000 on 2009-05-12
Try the "recovery mode option in grubs menu. 
Then restore the original file with 
cp your_backupfile.conf /etc/X11/xorg.conf

---

### Post by guedesav on 2009-05-12
Recovery mode is exactly the same system, but in single user mode, so it didn't work either.

What's happening is that my system is using the XFree86 server, instead of Xorg, and I want to make it use Xorg, not only its configuration file. I've already managed to get back to the previous screen resolution, but now my keyboard is messed, as I already said. Thus, I want to use Xorg, not XFree86 again.

Any other help (question mark)

---

### Post by andrea000 on 2009-05-12
Oh i have never used anything but x org 
Try the following

sudo apt-get install ubuntu-desktop

or  sudo apt-get install ubuntu-desktop --reinstall

That should re-install a fully featured desktop system

---

### Post by guedesav on 2009-05-12
I don't want to sound rude, but that exactly what I don't want to do...

By far I've managed to have my screen and keyboard configuration(though the screen is a still bit off...), but my xinput doesn't even work anymore...

---

### Post by andrea000 on 2009-05-12
I don't want to sound rude but then don't I'm done

---

### Post by mosaic2s on 2009-05-12
can you make a usb start up disk and boot through that?
then change the system settings.

---

### Post by guedesav on 2009-05-12
@andrea000 Thanks for the attention, it's quite possible that's what I'll have to do, anyway...

@mosaic2s What I need to know is exactly WHERE I need to change the settings so X.org, and not XFree86, is activated. I guess I won't even need a start-up disk if I know that.

PARTIALLY SOLVED: I've found a way, though I'm sure it's not the best. I've created a backup of my /usr/bin/XFree86 and then substituted it with a link to /usr/bin/Xorg. It worked, of course, but I still don't know where exactly is the configuration that says my system should be loading XFree86 instead of Xorg.

So, thanks for you all who took your time coming here to give some advice.

---

### Post by guedesav on 2009-05-13
I've finally found the actual solution for that. Here it is: find the X binary(probably in /usr/bin/X). It'll be a link to the X server you're using currently. So, just make it a link to your preferred X server, or, in my case:

```

ln -sf /usr/bin/Xorg /usr/bin/X

```

---

