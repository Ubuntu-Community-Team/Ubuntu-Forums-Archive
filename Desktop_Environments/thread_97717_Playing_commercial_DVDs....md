---
title: "Playing commercial DVDs..."
date: 2005-12-01
forum: Desktop Environments
---

### Post by furghella on 2005-12-01
I am new to Linux and Ubuntu. I have been playing around with Ubuntu 5.10 for a littel while and I am really impressed by this system. 

I am having a problem playing commercial DVDs, though. I have looked around, and read the relevant page (RestrictedFormats) in the Ubuntu Wiki. 

As far as I can tell I have  installed everthing that's needed to play encrypted DVDs. 
I have Windows XP installed on this PC as well, and with it I am able to watch DVDs, so I know that the DVD region code is correct. 

I tried Totem-xine, but I am not sure whether it is actually installed. The synaptic package manager says it is installed, but in the Applications menu I can only see Totem, not Totem-xine.

From Totem (or Totem-xine) I get the following error message:

Failed to play Audio/Video Disc
Failed to find mountpoint for device /dev/hdc in /etc/fstab

I am stumped - What am I missing?

Thank you very much for your help,

---

### Post by prawdapunk on 2005-12-01
you must install libdvdcss2

---

### Post by furghella on 2005-12-01
Libdvdcss2 is installed

---

### Post by aysiu on 2005-12-01
[QUOTE=furghella]
From Totem (or Totem-xine) I get the following error message:

Failed to play Audio/Video Disc
Failed to find mountpoint for device /dev/hdc in /etc/fstab

I am stumped - What am I missing?[/QUOTE] That's not a codec issue, that's a mounting issue. Why is it looking at /dev/hdc? It should usually be looking for something like /dev/cdrom or /dev/cdrom0...

---

### Post by furghella on 2005-12-01
Mmh, that makes sense, but what kind of device is /hdc and how can I change that?

---

### Post by aysiu on 2005-12-01
I'm not expert of CD-ROM drives, but I'll help you as best I can, and maybe someone else can pick up where I left off. First of all, can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by niobe_logos on 2005-12-01
To see what kind of device hdc is, open a terminal window, and check out the /dev directory:
```

niobe@logos:/dev$ ls -la hdc*
brw-rw----  1 root cdrom 22, 0 2005-12-01 10:00 hdc
```

To see where your DVD drive thinks it is, try this:

```
niobe@logos:/dev$ ls -la dvd*
lrwxrwxrwx  1 root root 3 2005-12-01 10:00 dvd -> hdc

```

To view the fstab file, you can open a terminal window, and enter this command:

```
cat /etc/fstab
```

You should get something like the following: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

If you don't have a line for /dev/hdc in this file, that could be your problem. Or, if the line's there, you want to make sure the correct locations are listed. If your drive is actually /dev/hde, you want to make sure the fstab file is correct.

Another thing you might do is install xine (xine-ui). Xine's advanced settings menu will let you point it explicitly to the drive as /dev/dvd.

---

### Post by furghella on 2005-12-01
The funny thing is, now it seems to work. I am not sure what brought about this change, but here is the information you asked for. In any event, I really appreciate your replying to my post.

sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12353    99225441    7  HPFS/NTFS
/dev/sda2   *       12354       24228    95385937+  83  Linux
/dev/sda3           24229       24321      747022+   5  Extended
/dev/sda5           24229       24321      746991   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10011    80413326    7  HPFS/NTFS


 df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              90G  2.1G   83G   3% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-10-386/volatile
/dev/hdc              7.8G  7.8G     0 100% /media/cdrom0


 cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by furghella on 2005-12-02
niobe_logos,

Something is wrong with my system. It worked yesterday, but no longer works today. 

I did what you auggested. Here is what happened:

/dev$ ls -la hdc*   and  /dev$ ls -la dvd* both have produced an error message (No such file or directory). However, the third command produced exactly what your were expecting:

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I also installed xine-ui, but it doesn't seem to make any difference. Is this a separate application? I can't find it anywhere.

---

### Post by niobe_logos on 2005-12-02
Hm. In another part of this thread, you had things working, but it wasn't clear if you'd changed anything or not. Did you make any changes to anything in the /dev directory, or in the /etc/fstab file?

If not, most likely nothing's permanently broken. Meantime, you can try telling Xine where your drive is.  To do this, start Xine, and hit ALT-s to bring up the settings menu. On the first tab, the "gui" tab, select "User Experience level" and select "Advanced". Click the "Apply" button.

Now select the "media" tab. Ignore 99% of the stuff on this tab, and take a look at the slot marked "device used for dvd playback".  Try putting in "/dev/hdc", let us know what the results are.

---

### Post by furghella on 2005-12-03
Ok, here is what I discovered:

I can watch encrypted DVDs but ONLY after I pop in a music CD and start SoundJuce (the default music player). If I don't do so Totem doesn't recognize the video DVD. The system thinks it's a data DVD , and doesn't display the DVD title. After I pop in the CD the DVD is recognized as a video DVD and its title is displayed correctly. After that Totem plays it.

Clearly SoundJuce (or whatever is called) starts something needed by Totem and/or the system, but what??

Also, I did install Xine using the synaptic package, but I can't find it anywhere. I think I have installed everything with Xine in the file name, but I couldn't find a new application by this name anywhere...

---

### Post by teppic on 2005-12-18
I can confirm the exact same situation - on a fresh install, video DVDs aren't recognised until an audio CD has been inserted. Not sure if there's a bug report on this or not.

---

### Post by doitashimashite on 2005-12-18
Maybe I missed something, but reading this thread I assume that you don't have a link to /dev/dvd, so what does

ls -l /dev/dvd

give you? It should give something like this:

lrwxrwxrwx  1 root root 8 2005-03-26 14:37 /dev/dvd -> /dev/hdc

But if it gives this instead:

ls: /dev/dvd: No such file or directory

then you should create a link yourself:

ln -s /dev/hdc /dev/dvd

See if this was the problem.

Good luck!

---

### Post by teppic on 2005-12-18
The link at /dev/dvd already existed. However, until a CD is placed into the drive, the system doesn't recognise video DVDs. Without changing any configuration at all, just inserting a CD corrects the problem.

---

### Post by furghella on 2005-12-20
the link is indeed there. This is what I get:

lrwxrwxrwx  1 root root 3 2005-12-20 20:29 /dev/dvd -> hdc

But Totem STILL cannot find the mountpoint if I don't play a CD first...

---

### Post by leech on 2005-12-20
[QUOTE=furghella]
I also installed xine-ui, but it doesn't seem to make any difference. Is this a separate application? I can't find it anywhere.[/QUOTE]

Xine-ui is another program (should be under Sound & Video -> Xine) Basically Totem-xine is just Totem using the xine backened (Otherwise no seperate program, it just uses the libraries from Xine instead of gstreamer, which doesn't work very well in Breezy).

I've never had many problems with playing DVDs in Ubuntu, generally after installing totem-xine then installing libdvdcss2 you should be able to just pop in any DVD and it'll automatically start Totem.  I know, I watched Star Trek last night with it :D

Xine uses /dev/dvd by default, so as doitashimashite said, you'll need to create that link if you try it there.  Good luck.

Leech

---

### Post by furghella on 2005-12-20
Well, Xine does work. The link is there, too. But Totem doesn't work...

---

### Post by teppic on 2005-12-20
Same here. Everytime I reboot I need to insert an audio CD before I can get Ubuntu to recognise the inserted DVD as a video DVD.

xine-ui does work whether or not an audio CD is inserted, but there's still a bug somewhere - Hal (or whatever) thinks it's a DVD-ROM when it's not, and Totem gets very confused.

---

### Post by furghella on 2005-12-21
Hal? What exactly is Hal?

---

### Post by teppic on 2005-12-21
The Hardware Abstraction Layer. It's used along wth dbus and udev to sort out hardware access consistently so you don't need to worry about creating obscure devices.

Somewhere along the line there's a bug which is telling the desktop wrong information about a DVD being inserted.

It doesn't seem to affect everybody though for some reason. I did a completely fresh install and the exact same problem occurs.

---

### Post by Craftycorner on 2007-05-26
I installed Ubuntu Studio, and it **looks** beautiful.  But it has bugs up the....

The program mounts **blank**. CD/DVD's just fine, and writes them successfully.   However, once written, they are useless because of the following bugs.

When I insert an audio CD, I get this error:
> Couldn't display "cdda:///dev/hdd".
There was an error launching the application.

When I right-click to eject, the program ejects the wrong DVD drive, (I've two, a writer & a player) the one containing **no** disc so I have to use the button to get that disk out of there.

When I insert a data CD/DVD or a video  CD/DVD I get this error:
> Unable to mount the volume '_____'.
Mount: No medium found.
This is true for commercial DVD's as well as they've the same structure.

This is a serious bug.  The fact that the sound recording is buggy as well doesn't help matters.

---

