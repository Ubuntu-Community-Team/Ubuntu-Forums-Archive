---
title: "Beep / Grip won't recognize CDs"
date: 2006-03-29
forum: Desktop Environments
---

### Post by illiterate_light on 2006-03-29
I'm having trouble getting certain apps to recognize that there is a CD in my drive.  The generic "CD Player" app recognizes audio CDs fine, and so does Sound Juicer.  But I actually want to use Beep Media to play CDs and Grip to rip them, and neither one recognizes audio CDs -- I just get "No playable CD found" in Beep, and Grip just doesn't acknowledge that there is a CD in the drive at all.  Any ideas?

Also, Grip briefly recognized a CD in the drive the first time I launched it, retrieved the tracklist and everything, but since then has refused to acknowledge any CDs (even the same one).

Any tips would be appreciated.

---

### Post by ispmarin on 2006-03-29
Did you try with xmms? xmms has a plugin for cd play, i think that is xmms-cdread. Don't know if beep need something similar...

---

### Post by siminone on 2006-03-29
In Grip, when clicking on the Config tab then CD sub-tab, what does the CDRom device say?

---

### Post by illiterate_light on 2006-03-29
[QUOTE=siminone]In Grip, when clicking on the Config tab then CD sub-tab, what does the CDRom device say?[/QUOTE]

Oh yeah -- meant to update my post with this.  Right now it shows /cdrom, which links to /media/cdrom.  I've tried it with both and neither works.  The strange thing is that it worked the first time I ran Grip, but hasn't worked since, and I haven't changed that setting (except to test if it worked any better with /media/cdrom, but only after it had stopped working).

---

### Post by siminone on 2006-03-29
remove entry and enter /dev/cdrom

---

### Post by illiterate_light on 2006-03-29
[QUOTE=siminone]remove entry and enter /dev/cdrom[/QUOTE]

Just tried that -- still says "No Disc."

I'm starting to think that something might have gotten deleted when I removed another sound app.  I just noticed that I'm getting a new error when I launch nautilus as the superuser, which my research tells me is related to CDs playing.  Here's the error:

(nautilus:30480): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

I tried reinstalling libgnomevfs2-0 based on a recommendation in another thread, but that didn't help (and I still get the error).  Any clues?

Also, I tried putting a DVD in the same drive, and I can browse the file contents in nautilus with no problem, but if I put a data CD or an audio CD in that drive, I see nothing.  But I can still view the contents of an audio CD in Sound Juicer, so I don't know what's going on.

---

### Post by siminone on 2006-03-29
I'm going to my kip soon but one last suggestion, in terminal type in 
                     more /etc/fstab

My fstab option for my cdrom is 

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

In the Ubuntu toolbar, click on System menu, then Administration sub-menu then Disks. This gives info on your CD-ROM drive.

---

### Post by illiterate_light on 2006-03-29
I get the exact same thing when I run fstab, and when I check System -> Administration -> Disks, it shows the drive as /dev/hdc.  It also shows that there is a disc in the drive, and gives me the option to play it, which works fine.  But I still can't see the CD in Beep or Grip.

Anyway thanks for the pointers... any other tips would be appreciated.

---

### Post by elamericano on 2006-03-29
Same boat here. The plugin is libcdaudio for both, and my configurations are identical in both players, but xmms works and bmp doesn't. BMP sucks!

Another interesting note is that when I test my settings for the bmp plugin, the drive spins, it counts 7 tracks and says digital audio extraction is enabled. When I browse to /media/cdrom0 it's empty. Maybe it would've played if I could've selected it!

Maybe it doesn't like the cdrom/cdrw combo drive.

---

### Post by illiterate_light on 2006-03-31
I found a solution, which was to ditch Grip altogether and install KAudioCreator.  Works awesomely, lots of control, and no headaches so far.  Also found K3B for burning CDs, which is better than anything I've used so far.

---

