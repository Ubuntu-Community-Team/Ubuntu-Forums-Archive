---
title: "Installing Grub. Quick Question."
date: 2009-06-23
forum: General Help
---

### Post by Roasted on 2009-06-23
I'm having some serious boot issues so I'm trying to reinstall grub through the Ubuntu LiveCD. I'm a little confused over something.

sudo fdisk -l yields the following

sda1 - * (boot) - NTFS (Vista)
sda2 - Extended
sda5 - Linux Swap
sda6 - Linux Root
sda7 - Linux Home

Shouldn't Grub be installed on the root partition?

When I run the command /find/grub/menu.lst it comes back with hd0,5. What is hd0,5? The Vista partition has the * mark for "boot"...

In short, where the heck do I install grub? hd0,5? hd0,0?

---

### Post by synapsys on 2009-06-24
Grub should be installed on the mbr of the hard drive unless you want to use the vista bootloader. (hd0,5) means the 6th partition of the first hard drive. Computers start counting at zero... not one.... If you want to use grub, install it to hd0. 

```
sudo grub
root (hd0,5)
setup (hd0)
exit
```

(the root command tells grub where to look for menu.lst)

---

### Post by Roasted on 2009-06-24
I know computer start counting at 0, I just didn't understand why the star was next to Vista for the boot.

Well, if that's the case, Grub is correctly installed - yet I am still having severe boot issues. This computer is about to go out the ******* window.

Anybody have any idea why there's times I'll boot up and get error 16, error 18, error 22, etc interchangably?

---

### Post by bumanie on 2009-06-24
If you want to dual boot with windows, boot live cd then go to terminal.
In terminal
> sudo grub > root (hd0,5) > setup (hd0) > quit Reboot and you should get the choice of booting from ubuntu or vista.

---

### Post by blackhawkover on 2009-06-24
Thanks so much. It helped a lot. I knew that windows would eventually get a little need for elbow room.

---

### Post by Roasted on 2009-06-24
I think Ubuntu is just corrupt. I ran the commands you gave me and everything worked fine. However, when I reboot, every single ******* time it says unclean shutdown, checking drives.

Then it comes back saying UNEXPECTED INCONSISTENCY - RUN fsck MANUALLY.

So, I do. It gives me errors but says it fixed them. I reboot.

Same error. Unclean shutdown, checking drives.

Guess what? UNEXPECTED INCONSISTENCY.

DJFAKLSDJFLASJDFKLAJSDFLKAJSDFKLAJSDKLFJASKLDFJASKLDFJASL

What do I do. Please tell me before I format and quit with computers.

---

### Post by synapsys on 2009-06-24
You may have a failing hard drive, maybe boot up the ultimate boot cd and run seatools to check if the hard drive is good. If the hard drive is good i would back up data and re-install ubuntu.

---

### Post by topher-t-mill on 2009-06-24
I am affraid you are not the only one, I had a dodgy update a while ago which, produced grub problems and I was unable to reconnect to the kernel, I had thankfully just downloaded slax and included gparted in the build, so I lifted all my important files to usb and an external drive, Ubuntu live wont 'allow' you to do simple things like that , permission denied etc.
I then re partitioned the drive to give me a bit more security, in case of a repeat disaster ( I do like Ubuntu ) and then reinstalled the whole caboodle. It did undergo a further kernel update but nothing went amiss this time.
I reckomend Slax, it is a very usefull distro  found at Slax.org

---

### Post by Roasted on 2009-06-24
> **synapsys said:**
> You may have a failing hard drive, maybe boot up the ultimate boot cd and run seatools to check if the hard drive is good. If the hard drive is good i would back up data and re-install ubuntu.

Oh, believe me - the hard drive is good. I sent back a perfectly good hard drive last month because of this same exact issue. I got a brand new hard drive, installed Vista/Ubuntu, everything seemed fine. BAM - More problems.

Looks like I'll be camping out in Vista for a while. What a ******* shitter.

I'm glad I have my data backed up though. I have a 2nd SATA drive in my PC I rsync my home directory to. I just hate reinstalling an operating system to fix it, unless it's Windows. I seriously just reimage all Windows computers cause the time required to fix them is unreal. But Ubuntu I always wanted to actually figure it out. Gahhhh.

topher - I'm sorry you didn't have any luck with the Ubuntu live cd, however, it works just fine when you use sudo with your commands. I have yet to find any limitations with Ubuntu when it comes to recovering data. :)

---

### Post by topher-t-mill on 2009-06-24
Thanks but when I try to use sudo (as root etc ) I still get 'permission denied' so I can't figure it out, and so  use  I Slax.

---

### Post by Roasted on 2009-06-24
> **topher-t-mill said:**
> Thanks but when I try to use sudo (as root etc ) I still get 'permission denied' so I can't figure it out, and so  use  I Slax.

The ONLY time I've gotten permissions issues when trying to recover data was when I tried to recover data from a Macintosh G5 computer. Other than that, it's been great for me. I wonder if you and I are doing anything different...

---

### Post by The Cog on 2009-06-24
If dound it as root gets yo upermission denied, it may still be mounted read-only because of the "unclean shutdown". I have seen this on a few occasions. I alwasys fixed it (so far) by running fsck from a live CD. Do it on both sda6 and sda7 to be sure.

---

### Post by Roasted on 2009-06-24
> **The Cog said:**
> If dound it as root gets yo upermission denied, it may still be mounted read-only because of the "unclean shutdown". I have seen this on a few occasions. I alwasys fixed it (so far) by running fsck from a live CD. Do it on both sda6 and sda7 to be sure.

That was exactly my problem. I was simply running sudo fsck, not sudo fsck /dev/sda6 and sda7. I booted up fine afterwards. Phew! I'm still having some boot issues though, but I think that's a separate issue... But I'll let that alone in its own thread.

[http://ubuntuforums.org/showthread.php?t=1182131](http://ubuntuforums.org/showthread.php?t=1182131)

EDIT - Also, I noticed I had an error with ZoneMinder (video surveillance system) around the time I saw the error to manually run fsck. Since I don't use ZoneMinder on this system (I was simply testing it but never got it running) I just did an apt-get remove --purge zoneminder to get rid of it. Now my system boots faster due to a lack of ZoneMinder processes that auto-start upon system boot and so far I haven't had any unclean shutdown issues... knock on wood.

---

