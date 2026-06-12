---
title: "DVD-ROM not recognized"
date: 2009-02-08
forum: General Help
---

### Post by RogDavies on 2009-02-08
I installed my DVD-ROM and smplayer but it does not list the drive in the drop down menu in the configuration screen. Same problem in VLC and movie player. I can play audio from the drive in rythmbox. There's obviously something wrong or missing in the configuration. CAnyone help a newbie know where to look for a solution. Have scoured the net and found nothing that I can follow.

---

### Post by SeanTater on 2009-02-08
Most Video DVD's are encrypted. The decryption codes are illegal in the US, but if playing commercial DVD's is important to you, you can run this in a terminal:

/usr/share/doc/libdvdread3/install-css.sh

And you should be able to play them.

Does that help?

---

### Post by RogDavies on 2009-02-11
Thanks,

tried that and no success. I've installed Power DVD for Linux and still no joy. I'm going to exchange the drive with a known , working DVD-ROM from another PC in case it's a hardare issue.

Rog

---

### Post by RedSingularity on 2009-02-11
Here folow [THESE]("http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/") steps.

---

### Post by RedSingularity on 2009-02-11
You really need the libdvdcss2 codecs.  I do fine without the other one but you can install it to be safe.

---

### Post by Dr Small on 2009-02-11
If you have libdvdcss2 installed, VLC should be able to play the DVD by opening the disc. Of course, if you're drive won't play it, then that is another problem.

---

### Post by mc4man on 2009-02-11
> I've installed Power DVD for Linux and still no joy.
That takes libdvdcss2 out of the equation

Either with the old drive or the new one, insert a dvd and then run
```
sudo lshw -C disk
```

This will tell you if the UDF file system is mounted properly and what the device node and /dev links are.

When you install the new drive while it will acquire the device node of the old drive (for example /dev/scd0)it will get one upped /dev links. (Previously assigned /dev links are reserved.

While this should present no problem to vlc or probably powerdvd, it can for apps that access from a default /dev link. (typically /dev/dvd and /dev/cdrom


It's best to reset your 70-persistent-cd.rules after settling on a drive your keeping.

---

### Post by rvm4000 on 2009-02-11
> **RogDavies said:**
> I installed my DVD-ROM and smplayer but it does not list the drive in the drop down menu in the configuration screen.

Notice that smplayer does not try to autodetect dvd devices. It just adds to the combobox the /dev/dvd* devices that are available in your system, but your dvd drive may actually be assigned to another device. In newer versions of smplayer it adds to the combobox more devices (like /dev/sr*) if available.

---

