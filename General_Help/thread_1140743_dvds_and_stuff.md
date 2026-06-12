---
title: "dvds and stuff"
date: 2009-04-27
forum: General Help
---

### Post by Nokes on 2009-04-27
this is just a quick question, is it possible to make it so that if removable media contains a file with a certain extension, it automatically starts a program?

---

### Post by mb_webguy on 2009-04-27
If you're talking about launching a certain application based on the type of media inserted, then sure.  In Nautilus (the file manager), go to Edit->Preferences, the Media tab, and use the drop-down boxes to select what application you want to use for each type of media.

If you're *not* talking about that, and actually want to open an application based on the file contents of the media, then...

Is it possible?  Yes.  Pretty much anything you can think of is possible.

Is it easy?  Well... it depends on your experience level, but if you're having to ask, then probably not.

You could write a script that runs whenever anything is mounted in the /media directory to scan the new device for files of that type and run a certain program if it finds one.  The script itself would be fairly simple, I think, depending of course on how many filetypes you want to handle.  (It's better to use mime types rather than file extensions, btw.)  As for where you'd put the script so that it would run whenever media is inserted...  that's a bit out of my depth.  Most of my experience with Linux is on servers, and you rarely have to do odd things with removable media with servers.

---

### Post by Nokes on 2009-04-28
well what i mean is, if i pop in a CD that has a .txt file, it opens the text editor

---

### Post by mb_webguy on 2009-04-28
Like I said, it's *possible*, but not necessary easy.  And woe upon you if you actually do this and plug in a USB drive with 100 different files of various types in its root directory...

---

### Post by nandemonai on 2009-04-28
> **mb_webguy said:**
> Like I said, it's *possible*, but not necessary easy.  And woe upon you if you actually do this and plug in a USB drive with 100 different files of various types in its root directory...

Exactly. This could turn out to be a nightmare depending how far you want to take it.

Something that perhaps scans for only music or video might not be too troublesome but then again implementation could be a pain for the user.

Think XP when you insert a 1TB external drive full to the brim with stuff.. 

"Scanning... Scanning... Scanning..."

I'd be interested to see what people come up with though :)

---

### Post by mb_webguy on 2009-04-29
[Here]("http://www.linuxquestions.org/questions/linux-desktop-74/running-a-script-when-auto-mounter-detects-usb-thumb-drive-insertion...-529113/")'s a thread on how you might go about doing this for a specific device.  I'm not sure how you'd detect the mount point for an unspecified device.

As for the script, you'd probably want to get the directory listing using "ls", then check the mime type of each file using "file --mime-type -b *filename*".  If the file is of the type you want to open, use "gvfs-open" to open it with the default application for that type.

---

### Post by Nokes on 2009-05-03
thanks, this just might be helpful!

---

