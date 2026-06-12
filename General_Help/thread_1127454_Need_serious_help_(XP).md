---
title: "Need serious help (XP)"
date: 2009-04-16
forum: General Help
---

### Post by scott1541 on 2009-04-16
I have done something to my xp home sp3 pc and when I boot in to windows from grub it says NTLDR missing, I think this has been caused by me trying to stop grub loading ( explained in one of my earlier posts) Now I need some help and advice on what to do ( xp won't load at all) HELP please!

---

### Post by Daisuke_Aramaki on 2009-04-16
> **scott1541 said:**
> I have done something to my xp home sp3 pc and when I boot in to windows from grub it says NTLDR missing, I think this has been caused by me trying to stop grub loading ( explained in one of my earlier posts) Now I need some help and advice on what to do ( xp won't load at all) HELP please!

See if this thread can help. It's fairly recent.

[http://ubuntuforums.org/showthread.php?t=1015116]("http://ubuntuforums.org/showthread.php?t=1015116")

---

### Post by scott1541 on 2009-04-17
Forget all this before stuff - now i have BIG problems, i adjusted some boot settings for xp in the menu.lst file, i restarted, selected xp and the recovery thing came up, went through it and selected restore to original settings. when it finnished i restarted and as soon a grub loads the whole system restart, this happens time after time after time and i cant access any operating system. What do i do, reinstall ubuntu or what?  any suggestions...

---

### Post by devosion on 2009-04-17
It sounds like the restore may have altered the MBR and grub's settings. If you have ubuntu's live cd i'd use it to boot up and access the drive, and reinstall grub. And the next time you can load Windows XP up dont let it restore. It may even be a good idea to back up your important data while that Live CD is in before you mess with anything from this point forward.

---

### Post by scott1541 on 2009-04-17
is there any way to uninstall grub instead, then i can format my external hard drive and wipe ubuntu so i can reinstall, because i think i did something wrong in the first place, i think i was supposted to make grub only install in the external drive, not the internal one as well

---

### Post by uncle-c on 2009-04-17
There is no need to reinstall anything just yet.
This is what I would personally do, but someone may have a better suggestion. You can fix your PCs MBR ( master boot record) by inserting a windows 98 boot floppy if you have one lying around or make one easily by following instructions from a guide on the net. You can using this boot floopy to fix your MBR by issuing the following at the command prompt [COLOR="Red"]fdisk /mbr[/COLOR] .
This will fix your boot record and then you should be able to boot into windows at least. Once you have sorted out your windows problems, then you can install grub to overwrite the mbr and then manually edit the menu.lst file ( to point to all the different OS you have on your system) in your linux installation. When installing grub to the MBR you will have to tell it where to find the linux install. You need a live cd for this. There is plenty of documentation about and it is a quite straightforward procedure. A common problem.

ps: You can delete grub by booting up a live cd and using the dd command.
The syntax of the dd command has to be absolutely 100% precise or you could destroy your partition table along with the boot record - so be aware !! This will render you PC unbootable and if you want to boot into windows you will have to fix the MBR using a windows boot floppy or a windows Installation cd.

---

### Post by scott1541 on 2009-04-17
Hmmmmmmmmmm....descisions descisions ...i could get a win98 boot floppy but i have no floppy drive to use it with.  What sort of stuff to you have to do with the dd cmd, i'm thinking that deleting grub might enable xp to boot normally and not get into a continuous restarting and booting loop

---

### Post by uncle-c on 2009-04-17
If you have Windows XP pro CD then you can boot up into the "Recovery  Console" and fix your MBR from there. It will automatically write over your grub and you should be able to boot into windows. Best try this method first.
You can use dd to delete the MBR but if you have no means of fixing the mbr or installing the Windows Boot Loader then you will have a problem booting into Windows. Hirens Boot CD, which you can download from the Net, has  fix MBR tools on it - it an an invaluable rescue CD and worth having : [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd).
Just for the record, deleteing the MBR using the dd command you  issue the following :

```

$ sudo dd if=/dev/zero of=/dev/hda count=1 bs=446
```

Your main hard drive may be /dev/sda depending on your hardware.

---

