---
title: "hibernate stopped working"
date: 2005-12-25
forum: General Help
---

### Post by exclipy on 2005-12-25
I have an Dell Inspiron 8600 with Kubuntu 5.10.  hibernate (using KLaptop) seems to suspend everything and shut the computer down properly, but on boot up, it seems to forget that it's in a hibernated state and just boots up normally.

It was working fine before I did a couple of things to the computer (I'm not sure which one broke it): I upgraded the kernel from the .24 package to the .25 package, and I messed around with the partitions, deleting my /home partition and changing the minor number of the / partition (hda5 now).  I'm thinking it was probably the latter which caused it, as I did have to fiddle with grub a fair bit before I could boot at all.

Here is what I see in /var/log/messages:
```
Dec 26 13:01:16 localhost kernel: [4294675.366000] Attempting manual resume
Dec 26 13:01:16 localhost kernel: [4294675.425000] swsusp: Suspend partition has wrong signature?
```
and then about 40 lines later:
```
Dec 26 13:01:16 localhost kernel: [4294678.348000] Attempting manual resume
Dec 26 13:01:16 localhost kernel: [4294678.363000] swsusp: Suspend partition has wrong signature?
Dec 26 13:01:16 localhost kernel: [4294678.395000] EXT3-fs: INFO: recovery required on readonly filesystem.
Dec 26 13:01:16 localhost kernel: [4294678.395000] EXT3-fs: write access will be enabled during recovery.
Dec 26 13:01:16 localhost kernel: [4294680.353000] kjournald starting.  Commit interval 5 seconds
Dec 26 13:01:16 localhost kernel: [4294680.353000] EXT3-fs: hda5: orphan cleanup on readonly fs
Dec 26 13:01:16 localhost kernel: [4294680.353000] EXT3-fs: hda5: 2 orphan inodes deleted
Dec 26 13:01:16 localhost kernel: [4294680.353000] EXT3-fs: recovery complete.
Dec 26 13:01:16 localhost kernel: [4294680.357000] EXT3-fs: mounted filesystem with ordered data mode.
Dec 26 13:01:16 localhost kernel: [4294683.111000] Adding 522072k swap on /dev/hda6.  Priority:-1 extents:1
Dec 26 13:01:16 localhost kernel: [4294683.305000] EXT3 FS on hda5, internal journal
```

Any ideas about what to do?

---

### Post by exclipy on 2005-12-26
Bump.

---

### Post by dcherryholmes on 2005-12-28
Yeah, bump it.  I'll wander over to the gentoo forums (my previous distro) and see if I can dig up anything useful.

---

### Post by Adrian on 2005-12-28
[QUOTE=exclipy]I have an Dell Inspiron 8600 with Kubuntu 5.10.  hibernate (using KLaptop) seems to suspend everything and shut the computer down properly, but on boot up, it seems to forget that it's in a hibernated state and just boots up normally.[/QUOTE]

I had a similar problem when I tried to hibernate from the Gnome logout screen. It was solved by doing it from the terminal instead. Maybe you could try that?

```

sudo -s
echo -n "disk" > /sys/power/state

```

---

### Post by GrumpyBob on 2005-12-28
I've had issues with hibernate possibly causing system hangs on my IBM Thinkpad Breezy install (I posted elsewhere about this).  I won't be using hibernate for the time being.  Does KDE use the same systems for hibernation as does Gnome?  

Robert

---

### Post by dcherryholmes on 2005-12-28
Heh.  Maybe my search-fu just isn't that great, but I struck out on the gentoo forums, went to a vanilla google search, and ended up pulling up the answer on ..... gasp!  The Ubuntu forums. :)

Anyway, the short of it is that it's a harmless error message, simply saying it hasn't found any suspend image on the suspend partition (i.e. swap).  I might expend a little more effort on supressing the output[1], but it appears to be benign.

[1] Ideally by finding out what this "splashy" thing is, and getting something smooth-looking laid over the blisteringly fast boot-god that is initng. :)

---

### Post by exclipy on 2005-12-28
Thanks for the replies everyone.

Adrian: That command doesn't halt the system for me.  It shows:
```
Writing data to swap (25169 pages)... done
Writing pagedir...done (99pages)
S|
Powering off system
Shutdown: hda
IDE device ACPI handler is NULL
```
and hangs there.  I forced the computer off and on bootup, it still had the same problem.

GrumpyBob: Yes, I think KDE just does what's in /etc/acpi/actions/hibernate, which is usually /etc/acpi/hibernate.sh.

dcherryholmes: Yeah, my problem is that it can't find the suspend image even when I suspend it.


A few more things I've thought of which might be causing it are:

[list]
[*] I'm not sending the right parameters to the kernel?  The entry in my menu.lst is:
```
title Ubuntu, kernel 2.6.12-10-686
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-10-686 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-686
savedefault
boot
```
Can someone with a working hibernate check this against theirs please?
[*] It might be mounting the swap partition too late.  I turned off the splash and this is what I see a few lines into the init:
```
Creating initial device nodes
Setting disc parameters
swapon: /dev/hda6: software suspend data detected.  Reinitializing the swap
Setting up swapspace version 1, size = 534605 kB
no label, UUID=...
Checking root file system...
```
[*] My swap partition is only a few megabytes bigger than my RAM (512MB vs 520MB).  But it doesn't throw any problems on suspension...
[*] I reinstalled my kernel image without recompiling the video driver so it doesn't recognise that it's the right suspend image?
[/list]

Can someone advise which one of these are likeliest/unlikeliest or how to check them please.  Thanks!

---

### Post by exclipy on 2005-12-30
Alright, I've sorted it out.  It turned out to be point number 1.  I had to add the kernel parameter resume=/dev/hda6 where /dev/hda6 is my swap partition.  ie. the line in /boot/grub/menu.lst became:
```
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda5 ro quiet resume=/dev/hda6
```

---

