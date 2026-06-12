---
title: "Big Copying annoyance in nautilus"
date: 2009-10-25
forum: Desktop Environments
---

### Post by maweki on 2009-10-25
Hello,

I think I'm running a rather common configuration (Jaunty, GNOME). The only "special" thing I did was getting to run a Dual-Head configuration with the proprietary ATI Drivers (small wonder).

There is a little annoyance. And I wonder whether it is my fault. I copy some 100 files from my HDD to a USB-Drive. And the USB-Drive is 2GB and my files are, let's say, 1.5GB (Only files, no folders).
Then some files are changed and I try to copy all files (via Drag and Drop) to the USB-Drive (because I dont want to move them all by hand).

And the reaction of nautilus (I guess) is, that he denies the action because the target drive is full. He did not start (as windows would) but he did also not check, if there are some files to be overwritten.

And even if the drive is full. I want him to just start and copy as far as he gets.
Is there any way to change this default behaviour?

Greetings
maweki

---

### Post by dv3500ea on 2009-10-25
That's strange, normally nautilus tries to merge folders of the same name and replace files of the same name. Have you renamed any of the folders? This would stop nautilus from merging folders and it would just copy them instead. Another possible issue is if the total size of the folders you are copying is greater than 2GB. You could also try deleting the files on the usb before copying the new files from the hdd. If none of this works you could run ```
rm -R /media/[usb name]/[location of files]
cp -R [path to files] /media/[usb name]/[location of files]
```

BTW, how do you know nautilus is male?:)

---

### Post by maweki on 2009-10-25
Sorry, I'm still drunk from yesterday (it's 11 am here) and my English starts to deteriorate with alcohol.

Nautilus does that with folders, yes. But say, (that's when I noticed) I have a playlist in Banshee. And I mark all songs and Drag and Drop them over on the usb drive.

Over a week or two, some songs are getting added but I don't really know (and care) which one. So I mark them all again and Drag and Drop them over (because I don't want to search for them in my home/music-folder) on the drive.
Nautilus does not check for duplicated files if I don't want to copy any folders.

If I want to have it fast, it is not a viable solution to delete all files. And using a terminal prompt is easy, I know. I use that for my backup procedures. But I just want to copy some music from a Banshee-playlist and it could not be harder.

(and also, as I said, if I just want nautilus to start and stop when the drive is full, there is no way. So I have to check how much space is on the drive, select the appropriate amount of data - which can be very tedious - and then copy it over).

---

