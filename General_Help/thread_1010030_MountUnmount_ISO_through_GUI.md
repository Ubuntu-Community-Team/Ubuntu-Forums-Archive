---
title: "Mount/Unmount ISO through GUI"
date: 2008-12-13
forum: General Help
---

### Post by montgoss on 2008-12-13
I watch DVD's from an ISO all the time.  Currently, I pull up a terminal and type that long mount command.  I'd like to be able to just double-click (or perhaps right-click) on an ISO in Nautilus and mount it. Then, I'd like to right-click on the new icon on my desktop and select "Unmount volume" and have it actually work.  This currently throws the error "umount: /media/dvd_iso is not in the fstab (and you are not root)".  

This leads me to believe there is something I could add to the fstab so Ubuntu would automatically know to mount ISO's to /media/dvd_iso and allow me to unmount them.  Is this true?

I did create a simple shell script that contains the mount command ("mount $1 /media/dvd_iso -t iso9660 -o loop") and then I did an "Open with" and used a custom command of "gksudo /home/montgoss/mount.sh %S".  That works as far as the double-click to automount.  But I still have to use a terminal to unmount.

Is there a better way to do this?

Thanks in advance.

---

### Post by binbash on 2008-12-13
[http://www.getdeb.net/app/AcetoneISO](http://www.getdeb.net/app/AcetoneISO)

---

### Post by montgoss on 2008-12-13
> **binbash said:**
> [http://www.getdeb.net/app/AcetoneISO](http://www.getdeb.net/app/AcetoneISO)

Thank you for the suggestion, but that's not really what I'm looking for.  While that app works, it takes even longer than using the terminal.  I'm looking for something that's completely transparent.  Not a separate app that is just a wrapper for the command that takes me 10 seconds to type.

---

### Post by drs305 on 2008-12-13
> 
But I still have to use a terminal to unmount.
Is there a better way to do this?


My guess is there is still a better way to do this, but I got the user unmount part solved by first mounting a specific, existing, iso from within fstab. I could then mount any other iso file using the command line (or your script) and could unmount it by right clicking in nautilus or on the desktop icon.

The line I added in fstab was:
```

/path.to.existing.iso/file.iso /media/dvd_iso iso9660 ro,loop,auto 0 0
```

---

### Post by El_Belgicano on 2008-12-13
2 fast idea's:

**1) VLC/mplayer**
If I'm not mistaken, VLC can handle dvd-iso's directly...
"open" > "file" > -your-iso-image-
You don't even have to mount it.
I know mplayer can do it...

**2) Aliasing**
Try an to create an alias in your .bashrc for the mount command.

---

### Post by blakjesus on 2008-12-13
Try [this tutorial]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html") out.

It uses a nautilus script to mount and unmount .iso files from the right click menu. Can't get much easier than that, and it works perfectly for me.

---

