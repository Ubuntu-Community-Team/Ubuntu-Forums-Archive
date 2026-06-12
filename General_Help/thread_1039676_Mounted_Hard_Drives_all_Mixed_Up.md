---
title: "Mounted Hard Drives all Mixed Up"
date: 2009-01-14
forum: General Help
---

### Post by MTGap on 2009-01-14
Okay well it all started with trying to automatically mount an internal hard drive (Ubuntu is running off an external) I'm pretty sure I've got it to work with adding this line to fstab:

```
/dev/sda2	   /media/Windows  ntfs	 defaults  0  0
```

Here is the rest of it:

[IMG]http://i537.photobucket.com/albums/ff339/AgentGap/HDD2.png[/IMG]


Now I've done other methods and it seems I've messed everything up:

[IMG]http://i537.photobucket.com/albums/ff339/AgentGap/HDD.png[/IMG]

So first off sdc1 is blank... that is the external hard drive (the boot up ubuntu one) I'm pretty sure. Nothing is in it. I don't want it there. How can I get rid of it?

Then there are duplicates of these:

Windows = disk
External = sdb1

Oh and then there is the cdrom shortcut or whatever... how did that get there?

I'd prefer if there was only one of these... so how can I fix all these problems that I have. I'm really mad at Ubuntu now for how freakn' hard it is to automatically mount a hard drive and manage them... :-x


> I went into nautilus with admin rights and deleted the cdrom shortcut and blank folder, I still need help with the others because I want the icons to be HDDs and show up on the desktop...

---

