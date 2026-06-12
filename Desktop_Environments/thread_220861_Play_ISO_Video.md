---
title: "Play ISO Video"
date: 2006-07-22
forum: Desktop Environments
---

### Post by nami on 2006-07-22
Hi

Is it possible to copy a dvd as an ISO and play it directly from your harddrive as an ISO file?

---

### Post by it.henrik on 2006-07-22
It should be .. at least with VLC .. vlc is a power tool.

---

### Post by SimonJW on 2006-07-22
VLC or Mplayer or Xine may be able to play an ISO like it was a DVD.

But if they can't, you can simply mount it:
```

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop

```

then point your DVD player of choice to it, pretending like it is an actual DVD, and unmount it when done:
```

sudo umount /media/iso/

```

There is a Nautilus Script floating around the forums somewhere to make this even easier.

Hope this helps

---

### Post by nami on 2006-07-22
Thanks, I will give that a try.

---

### Post by patrickthebold on 2006-07-22
Most players should work if you just point them to the iso.  

In gxine file->Configure -> Preferences -> Media -> dvd Then change the device field to /path/to/iso 

you might have to change your experience level to see all the tabs.

---

### Post by nami on 2006-07-29
Ok, I made some iso's mounted them and played them, but for some reason they will not start playing from the beginning and will only play 1 chapter, they will not go to the next chapter?

---

### Post by smyrman on 2008-03-29
To open with xine:
just write this in a console (or in the ALT+F2 menue):

```
xine "dvd://path/to/my/file.iso"
```


To open with mplayer:
rigth click the iso, choose "open with" and write "mplayer".

or write this in a console:

```
mplayer "dvd://path/to/my/file.iso"
```

To open with dragonplayer (KDE 4):
write this in a console:

```
mplayer "dvd://path/to/my/file.iso"
```

Hopes this helps=)

---

