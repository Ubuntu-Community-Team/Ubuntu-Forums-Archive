---
title: "HELP! Chmod'd sudoers and now I can't edit to fix or sudo"
date: 2008-12-20
forum: General Help
---

### Post by UbuObsidian on 2008-12-20
Ahhhh!!!, I didn't realize there was a command for specifically doing this but I needed to edit sudoers and chmod'd it to edit, and now I can't do anything that I know of to fix it. Is there a way to login Ubuntu as root to set sudoers back to 0440?!

---

### Post by Rocket2DMn on 2008-12-20
You can reboot into the recovery mode kernel (second option at the GRUB screen), enter the root console and reset the permissions:
```
chmod 440 /etc/sudoers
```
Of course, it needs to be owned by root:root
Then you can reboot normally
```
reboot
```

---

### Post by UbuObsidian on 2008-12-20
GRUB screen? What that? :(

I guess I should've mentioned I'm running Ubuntu on the Ps3. I'm not aware of any grub screen. *wails*

Thanks for the reply btw, much appreciated.

---

### Post by Rocket2DMn on 2008-12-20
The GRUB screen is the black screen that appears near the beginning of the boot sequence, where you select your kernel.  I would expect you get this on a PS3, but I've never actually seen Ubuntu on a PS3 myself.

---

### Post by UbuObsidian on 2008-12-20
There's kboot on the PS3, that's similar I guess?, but there's nothing really other than this string to run Ubuntu. /boot/vmlinux initrd=boot/initrd=/boot/initrd.img root=/dev/ps3da1 The kboot.conf file in /etc does appear to be able to boot a back up, but there's no way for me to see the kboot.conf as I can't use sudo even in kboot and I can't use bash to become root and chmod back to 440. I get a 'read only' file system error and binaries can't be run.

---

### Post by albinootje on 2008-12-20
> **UbuObsidian said:**
> There's kboot on the PS3, that's similar I guess?, but there's nothing really other than this string to run Ubuntu. /boot/vmlinux initrd=boot/initrd=/boot/initrd.img root=/dev/ps3da1 The kboot.conf file in /etc does appear to be able to boot a back up, but there's no way for me to see the kboot.conf as I can't use sudo even in kboot and I can't use bash to become root and chmod back to 440. I get a 'read only' file system error and binaries can't be run.

According to this :
[http://www.yellowdog-board.com/viewtopic.php?t=1678&highlight=single+mode](http://www.yellowdog-board.com/viewtopic.php?t=1678&highlight=single+mode)
You would try :
```

linux 1

```
For "recovery mode".

---

### Post by UbuObsidian on 2008-12-20
That didn't work here, it booted into my normal account. I ran sudo in the terminal and still got the 'sudoers needs to be 440' error.

---

### Post by taurus on 2008-12-20
Can you boot it with the LiveCD?

---

### Post by UbuObsidian on 2008-12-21
I didn't use a live cd. I think I'm stuck.

---

### Post by albinootje on 2008-12-21
> **UbuObsidian said:**
> I didn't use a live cd. I think I'm stuck.

Is there an Ubuntu installation cdrom for PS3 ? Or do you need to install from usb ?

---

### Post by UbuObsidian on 2008-12-21
I installed it from the guide here:

[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

Here's the iso I used: 

[http://cdimage.ubuntu.com/ports/releases/7.10/release/ubuntu-7.10-alternate-powerpc+ps3.iso](http://cdimage.ubuntu.com/ports/releases/7.10/release/ubuntu-7.10-alternate-powerpc+ps3.iso)

---

### Post by albinootje on 2008-12-21
> **UbuObsidian said:**
> I installed it from the guide here:

[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)


Okay. Looking at the section "Booting Back to the XMB", can you try :
```

boot-game-os 1

```

---

### Post by UbuObsidian on 2008-12-21
Umm.. booting back to XMB isn't my problem. I can't use sudo in Ubuntu remember?

---

### Post by albinootje on 2008-12-22
> **UbuObsidian said:**
> Umm.. booting back to XMB isn't my problem. I can't use sudo in Ubuntu remember?

The added "1" at the boot prompt is meant to boot up in "recovery mode", where you will become "root", and thus sudo is not needed.
Did you try it, and did it boot as normal, or ?

---

### Post by mcmuzz4 on 2009-08-23
I had a similar problem from modifying sudoers, and could not sudo at all, and found a solution to the problem.
 
(i put a # in front of "%admin ALL=(ALL) ALL" and blocked my account from admin group...whoops) 
 
Fixed it by downloading pdaXrom [http://wiki.pdaxrom.org/index.php/Bootable_CD_for_PS3](http://wiki.pdaxrom.org/index.php/Bootable_CD_for_PS3) a small approx 70MB download, bootable ps3 linux live CD.
 
Once i had booted into the pdaxrom live CD i was able to change the /etc/sudoers file back to how it was supposed to be, rebooted into xubuntu ps3 and everything was all good!!!
 
Hoorraah!! Did not have to reinstall linux!! :guitar:i just spent forever all weekend setting it up too... i'm a linux noob!

---

