---
title: "Moving /home"
date: 2005-11-25
forum: Desktop Environments
---

### Post by Karlos on 2005-11-25
I moved my /home directory using the rsync method explained in this thread
[http://www.ubuntuforums.org/showthread.php?p=506910#post506910]("http://www.ubuntuforums.org/showthread.php?p=506910#post506910")
all has gone well and my /home is now located on another hard drive (hdb) to allow more space.

But .. I can't figure out how to delete the old /home (hda)

any ideas?

---

### Post by Egree on 2005-11-25
Can't you just remove it with *sudo rm -rf /home*?

---

### Post by Karlos on 2005-11-26
I don't want to delete my new /home.
I suppose what i'm trying to work out is how to isolate my old home to be deleted.
is it better to use a live cd or system rescue cd??

---

### Post by Xian on 2005-11-26
Rename it to something like home_old and then remove it.

---

### Post by Karlos on 2005-11-28
i'm sorry but I still don't get it :confused:.. the only /home I can find on my system is on hdb. But looking at disc-usage the old information from my old home is still there(hda).

I can't seem to find a way to access it .. the only home that shows up is the hdb one .. which is good, it means that it's all working as I want it too .. But I wanna install more programs and stuff  and I need to make room. i'm confused (story of my life):???:

---

### Post by tedius on 2005-11-28
Was your old /home on the same partion as your / ?

Before you start I would back up you /home just encase every thing goes wrong!

If it was you need to do the following

sudo umount /home
ls /home (You should now see you old homes stuff)

Note: Be very careful here.

sudo -rf /home/*
sudo mount /home

You will now have deleted your old /home and remounted you new one.

If you old /home was on a different partition you will have to mount this before you do the rm and then unmount it.

Remember to backup you /home dir before you do start anything, just encase it all goes wrong.

Tedius

---

### Post by Brent Dax on 2005-11-28
[QUOTE=Karlos]But .. I can't figure out how to delete the old /home (hda)

any ideas?[/QUOTE]
I don't think you can do it in normal mode, because various programs will be keeping various files open in your home directory.  Instead, you'll need to drop to single-user mode.

1. Reboot.  At the GRUB boot screen, choose rescue mode.
2. Wait for it to boot.
3. Make sure your new /home is unmounted: "umount /home"  Don't worry if this complains that there's nothing mounted there.
4. Delete /home: "rm -rf /home"
5. Re-create it so you can mount onto it later: "mkdir /home"
6. Reboot: "shutdown -r now"  Allow GRUB to boot normally this time.

---

### Post by Karlos on 2005-11-29
many thanks .. it is all starting to make sense, ie: unmounting my new home first, which is on hdb2.
presumably in that case then umount /home would be the same as umount /dev/hdb2?

---

### Post by erjohan on 2005-11-29
Yes you are right, it's the same thing. You type mount and it says "/dev/hdb2 mounted on /home" then you can both do; "umount /home" and "umount /dev/hdb2". But if you have several filesystems mounted on /home you have to use "umount /dev/hdb2"

---

### Post by Karlos on 2005-11-30
yep, all sorted.. thanks all
may I suggest a how-to on moving /home
I don't know if one already exists
may have a go at it meself when I get a chance ... ! :rolleyes:

---

