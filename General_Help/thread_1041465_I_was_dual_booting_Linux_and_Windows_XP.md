---
title: "I was dual booting Linux and Windows XP"
date: 2009-01-16
forum: General Help
---

### Post by Spen on 2009-01-16
I had Windows XP installed on one HDD, then installed Linux on another HDD

I did everything on Linux to get it to dual boot, now foolishly I went and reformatted the Windows XP partition and reinstalled Windows.


I no longer have the boot menu to get into Linux, and I really don't want to reinstall Linux again and lose everything.

Is there anyway I can dual boot again?

Thank you.

---

### Post by taurus on 2009-01-16
You just have to reinstall GRUB to MBR so you can boot both Ubuntu and windows again.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Spen on 2009-01-16
Even if I have Linux on another hard drive?

---

### Post by LowSky on 2009-01-16
yes, best thing to do is make the linux drive the primary boot drive so it doesn't touch the Windows MBR, you can do so from your BIOS

Then get the super grub CD and use that to repair grub for ubuntu, or use the Ubuntu Live CD and repair your Grub file by hand.

---

### Post by jnw222 on 2009-01-16
in short 
it seems that the windows hdd is primary

so boot of any livecd with the grub package 
terminal

```
grub
```
```
find /boot/grub stage1
```
```
root (hd1,0)
```
i presume /dev/hdb1 or /dev/sdb1 (both are (hd1,0) is the ubuntu partition)
```
setup (hd0)
```

---

### Post by Spen on 2009-01-16
Thanks for all the help guys!

I'll try this once I find my CD...

---

### Post by Spen on 2009-01-16
> **jnw222 said:**
> in short 
it seems that the windows hdd is primary

so boot of any livecd with the grub package 
terminal

```
grub
```
```
find /boot/grub stage1
```
```
root (hd1,0)
```
i presume /dev/hdb1 or /dev/sdb1 (both are (hd1,0) is the ubuntu partition)
```
setup (hd0)
```

I get this error when using find /boot/grub stage1

```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub stage1

```

---

### Post by Spen on 2009-01-16
I really hope I can fix this, I don't want to lose everything to windows

---

