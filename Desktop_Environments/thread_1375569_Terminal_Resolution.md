---
title: "Terminal Resolution"
date: 2010-01-08
forum: Desktop Environments
---

### Post by Askar450 on 2010-01-08
I'm trying to make get a higher resolution when I use Ctrl+Alt+F2, I've looked up in other forums but apparently 9.10 changed its methods to fixing your desired resolution. I've tried other ways of changing it but I get an error when I boot in to the system, I have Ubuntu 9.10 64-bit, a GeForce 8800m GTS, the highest my screen can go is 1440x900. Any help would be appreciated, thanks.

---

### Post by kellemes on 2010-01-08
Does this help?
[https://wiki.ubuntu.com/FrameBuffer]("https://wiki.ubuntu.com/FrameBuffer")

---

### Post by Askar450 on 2010-01-08
I've tried that but my menu.lst is empty so I don't know what to do from there on. I am missing a step or something?

---

### Post by nothingspecial on 2010-01-08
The file you need to edit is /etc/default/grub

---

### Post by Askar450 on 2010-01-08
I've done the /etc/default/grub already I just get a message saying the vga=775 is incorrect or something the message moves too fast for me to read.

---

### Post by nothingspecial on 2010-01-08
In /etc/default/grub find 

    ```
GRUB_GFXMODE=1440x900@32
```

underneath that line put

    ```
GRUB_GFXPAYLOAD=1440x900x32
```



in /etc/grub.d/00_header find 
```

    if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=1440x900x32 ; fi
```


then underneath it put
```

    if [ "x${GRUB_GFXPAYLOAD}" = "x" ] ; then GRUB_GFXPAYLOAD=1440X900x32 ; fi
```

Then find the line

    ```
set gfxmode=${GRUB_GFXMODE}
```
below it put

    ```
set gfxpayload=${GRUB_GFXPAYLOAD}
```

Then ```
sudo update-grub2
```

Obviously change the lines to your own resolution.

I found this on the debian forums somewhere.

---

### Post by Askar450 on 2010-01-08
I did what you typed up nothingspecial but it only changed the resolution on my grub, if I use Ctrl-Alt-F2 its still the same resolution.

---

### Post by SecretCode on 2010-01-08
Try the vga= method, with whatever value you need, but change *linux* and *initrd* to *linux16* and *initrd16* as described here:
> **SecretCode said:**
> The grub2 official method appears to be setting the *gfxpayload* option, either to 'keep' or to a specific value. However, no values produced useful results - the login messages and the TTYs either defaulted back to 640x480, or were black or a garbled mess of colours.

The older way is adding '*vga=*' to the boot options, but grub2 says this is deprecated, and it doesn't work for most values. I got halfway by setting vga=792, making sure 'quiet splash' were *not* present, and ignoring the deprecated message. Then I got a 1024x768 resolution for login and tty consoles. Other values just got low resolution.

But the best result was by changing the boot commands in /etc/grub.d/10_linux from 'linux' and 'initrd' to '**linux16**' and '**initrd16**'. Then setting the boot option "**vga=865**" in GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub - and including "quiet splash" or not, it doesn't matter - I am able to get full native resolution of 1280x800, both in login console messages (visible if "quiet" isn't specified) and in TTYs 1 - 6. :) :D

If anyone is tempted to try this out, check what video modes your card supports via ```
sudo hwinfo --framebuffer 
```and get the mode number from the line you want - I used Mode 0x0361 which is 865 decimal. You can probably set the boot option vga=0x0361 directly.

And **remember** after any changes to run ```
sudo update-grub
```



---

### Post by Askar450 on 2010-01-08
I change all of them?

---

### Post by SecretCode on 2010-01-08
All of what? If you mean all occurrences of linux and initrd, I only changed them in the first menu item - I left the recovery item as is.

---

### Post by Askar450 on 2010-01-12
I must have done something wrong cause it didn't work, If anyone can still help me I'd appreciate it.

---

### Post by encompass on 2011-01-19
Does it show up as a normal boot or does it give any errors.  "Didn't work is like telling someone that "Car doesn't work, fix it." And your both on the phone.

---

### Post by shmeeter on 2011-05-06
Hi.  Just fixed this myself, and I found this post looking for a different problem...

Change the **/etc/default/grub** file.  I added "video=1600x1200-32@85" to the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet video=1600x1200-32@85"
```

Substitute your desired resolution, etc.  Don't forget to run ```
sudo update-grub
``` after that.

**If that doesn't work alone:**

For me this was honestly a bunch of flailing when it worked, and somewhere along the line I un-blacklisted the vesafb driver or whatever, too.  I'm not positive this was necessary, but if the above doesn't work alone, try this, too.  As root, edit the file **/etc/modprobe.d/blacklist-framebuffer.conf**, and comment out the line 
```
# blacklist vesafb
```
(I am about to experiment with intelfb, too.)
Then add the lines
```

fbcon
vesafb

```
to the file **/etc/initramfs-tools/modules**.  Afterward you will need to do ```
sudo update-initramfs -u
```

Probably need to reboot after that.  I read this on some other blog somewhere, can't remember where, and it worked for me.  Now if I can only fix the resolution in X...

---

