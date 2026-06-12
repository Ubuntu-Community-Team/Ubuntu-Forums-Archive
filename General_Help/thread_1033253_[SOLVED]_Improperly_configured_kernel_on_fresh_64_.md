---
title: "[SOLVED] Improperly configured kernel on fresh 64 bit dm-crypt 8.04.1 install?"
date: 2009-01-07
forum: General Help
---

### Post by MaddMatt on 2009-01-07
Hi All, 

So I'm a little masochistic, apparently, and I tried to do a fresh install over my existing dm-crypt (LUKS) encrypted system about a month ago - switching from 32 bit 8.04 to 64 bit 8.10. (Hardware: Macbook Pro Penryn 4,1)  You can check out this thread to read more about that:
[http://ubuntuforums.org/showthread.php?t=1021172](http://ubuntuforums.org/showthread.php?t=1021172)

In any case, I was finally able to get the darn thing to install yesterday using a 8.04.1 64 bit alternate disc. The problem is that the kernel seems to be doing a soft-hang before actually unlocking the hard disc. This seems to be an issue related to the 'usbcore' module, as far as I can tell as per this line in the output (from recovery boot)

(The following is the gist of the message.)
```

[ 38.959995] usbcore: restered new interface driver usbhid /build/buildd/linux_2.6.24
[ 38.9600923 ] v 2.6 usb hid core driver drivers/usbhid/hid.core. etc......
```

at which point it does nothing, until I hit cntrl+alt+del, which it responds to. 

If I have USB hard drives plugged in it goes past these last messages to talk about some sdb mumbo, but essentially the same thing happens - it never gets to the point where I can unlock my hard drive. 

I would be willing to disable USB from the kernel if I knew how just to see what happens. 

I don't think this is related to the dm-crypt, but maybe a poorly configured module of some sort- but I'm not a kernel expert at all. I'd appreciate any ideas, as I'm in serious linux-withdrawal right now. 

Cheers, 
M

---

### Post by MaddMatt on 2009-01-08
Hi All, 

A. What I have realized in the last few weeks is that Ubunu forums is great for small little questions, but when anything super technical comes up, no one steps to the plate. 

B. I screwed around with the config file from the /boot directory, and changed all of the USB entries there to reflect my last configuration (I had a pre-reinstall-backup). 
Maybe as a result of this, or maybe just due to patience, I left my computer booting and returned to find this: 

ALERT! /dev/mapper/MtOlympus-root does not exist. Dropping to a shell!

So apparently this is some sort of misconfiguration. My menu.lst looks the same as when I had it installed as a 32 bit 8.04 dm-crypt system... so I don't think it has to do with menu.lst. Does anyone know if the kernel is configured specially to handle dm-crypt systems? Maybe installing from the 'repair' mode on the alternate CD doesn't configure the kernel properly. 

This post may need to get moved to security? 

Cheers
M

---

### Post by stream303 on 2009-01-08
[edit] removed reply.

---

### Post by Joeb454 on 2009-01-08
Moved at OP request :)

---

### Post by hyper_ch on 2009-01-08
you need to create an initrd that contains cryptsetup dm-crypt and loads the aes, dm-crypt and dm_mod modules... that is required to unlock the harddisk.

---

### Post by MaddMatt on 2009-01-08
DELETED: Duplicate Post

---

### Post by MaddMatt on 2009-01-08
Thanks hyper_ch! I much appreciate the information!

In a rescue-shell I checked /proc/modules and found all 3 that you mentioned, so that wasn´t the issue, actually. However, the folks on the dm-crypt mailing list turned me on to this: the 8.04.1 alt-install disk didn´t create a /etc/crypttab file. SO it was a pretty straightforward fix after that.  

The Step-By-Step Solution: 

1. Waited for the boot to time-out and the busybox terminal to load 
2. ran cryptsetup:
```
cryptsetup luksOpen </dev/my-partition> <name-of-map>
```
3. Exited the busybox terminal, which finished the boot. 
4. Once the boot was finished, I properly configured the /etc/crypttab file
5. And then I updated the initrd:
```
sudo update-initramfs -k all -c -v
```

So thank you very much for stepping up with the info! 

I´m going to sit down and write a HOWTO about this, because frankly doing the install/upgrade from 32 bit LUKS to 64 bit has been the single biggest pain-in-the-a$$ since before I was using Feisty... Sheesh!

---

### Post by MaddMatt on 2009-01-09
I finished everything and wrote a howto here: [http://ubuntuforums.org/showthread.php?p=6520811](http://ubuntuforums.org/showthread.php?p=6520811)
Please let me know if you see changes. Thanks!

---

