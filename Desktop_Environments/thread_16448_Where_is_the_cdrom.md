---
title: "Where is the cdrom?"
date: 2005-02-21
forum: Desktop Environments
---

### Post by Biffy on 2005-02-21
Let's say i want to play an audio-cd on my Ubuntu system. I am using xmcd and it needs to know where the cdrom is. I am used to it being in /dev/cdrom , but this is not the situation in Ubuntu. Where is it located?

I have discovered, that if i have a data-cd, i can mount it by typing: mount /media/cdrom . That works fine, but xmcd says that /media/cdrom aint the correct location. Neither does any other cd-playing software.

I am using Fluxbox so there is no auto-mounting going on.

---

### Post by Ste on 2005-02-21
Mine is /media/cdrom0
The zero at the end being important. Try that if it don't work come back and let us know.


[edit]Seems the audio cd's don't get mounted. It did play under gnome-cd tho,[/edit]

---

### Post by KLineD on 2005-02-21
Or just look at the /media folder and do a ls -al to see where those symbolic links are pointing to and that's where your cdrom is.

---

### Post by Biffy on 2005-02-21
Yeah, it links to /media/cdrom0 . As i typed in my first post, i do mount data-CD's there. That's weird, because audio-applications says that /media/cdrom0 isnt the correct path.

This is what xmcd says:

```
/media/cdrom0 is not the correct special device type!
```

---

### Post by kassetra on 2005-02-21
As crazy as this sounds, this is what my audio applications tell me I'm using to access my cdrom:

/dev/cdrom

Just the device, not mounted.  Yes, my cds play and rip just fine as well.

---

### Post by Biffy on 2005-02-21
Weird! Maybe i'll have to create it.

---

### Post by kassetra on 2005-02-21
[QUOTE=Biffy]Weird! Maybe i'll have to create it.[/QUOTE]

You shouldn't have to create it... you should already have /dev/*  Those are the physical devices.

Maybe try telling your cd player to look for an audio cd in /dev/cdrom...

---

### Post by Biffy on 2005-02-22
[QUOTE=kassetra]You shouldn't have to create it... you should already have /dev/*  Those are the physical devices.

Maybe try telling your cd player to look for an audio cd in /dev/cdrom...[/QUOTE]

I can find everything except the cdrom in /dev. If i tell xmcd to use /dev/cdrom, i get the same error message as i typed above.

---

### Post by kassetra on 2005-02-22
[QUOTE=Biffy]I can find everything except the cdrom in /dev. If i tell xmcd to use /dev/cdrom, i get the same error message as i typed above.[/QUOTE]

Ok, on my system, /dev/hdc is the actual device for my cdrom and /dev/cdrom is just a symbolic link to that device.
Since you have to mount everything by hand, you probably know the actual device for your cdrom (I'm hoping), most likely, it's /dev/hdc
Make a link to it called /dev/cdrom by typing this in a command line:
 ```
ln -s /dev/hdc /dev/cdrom
``` 

Then try an audio cd (without mounting)

---

### Post by Biffy on 2005-02-22
I checked it out, and my CD-rom is in /dev/hdd and links to /media/cdrom . Then, /media/cdrom links to /media/cdrom0 . Kinda weird.

Well, by typing in /dev/hdd in cd-playing software such as xmcd and kscd, it plays the CD fine. :)

Thanks for your help.

---

### Post by kassetra on 2005-02-22
[QUOTE=Biffy]I checked it out, and my CD-rom is in /dev/hdd and links to /media/cdrom . Then, /media/cdrom links to /media/cdrom0 . Kinda weird.

Well, by typing in /dev/hdd in cd-playing software such as xmcd and kscd, it plays the CD fine. :)

Thanks for your help.[/QUOTE]

Wish I could have helped faster!  :)
But at least you can play cds now!
(yeah, /media/cdrom to /media/cdrom0 *is* kinda weird...)

---

