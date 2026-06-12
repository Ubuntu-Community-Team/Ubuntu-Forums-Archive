---
title: "F-spot wont import all photos (no error given)"
date: 2006-08-08
forum: Desktop Environments
---

### Post by finite9 on 2006-08-08
I imported (without copying the files to the photos folder--i want to keep them in their original location) all my photos on a fat32 partition into f-spot on ubuntu 6.06 but the timeline bar at the top only shows a small subset of the photos I imported.  Like, I have lots of folders full of images taken over several months during 2006 but f-spot only shows photos upto october 2005 and doesnt show *all* photos from 2005 either!  I dont understand why its only importing a random subset of my photos.  Does anyone have any ideas?

--finite9

---

### Post by orb9220 on 2006-08-08
Well if my memory serves me. I seem to recall that it was because of the images being on a fat32 partition. Amd also about special characters and ultra-long filenames.

If you could the only way to confirm would be to copy them to ext partition with nautilus then clear f-spot databse and reimport them from there.

Or check your file names.

Sorry I can't be more help.

---

### Post by finite9 on 2006-08-08
thanks for the tip - it must be the folder names that are too long, as the file names are all "IMG_14045.jpg" - I do not change file names when importing from my Canon IXUS, but my folder names are all custom named.

I will try changing folder name first then if that fails, move the folder (with new name) to my jfs partition.

--finite9

---

### Post by warjowuch on 2006-10-02
I have got a similar problem. In my case, f-spot does not import certain pictures I physically rotated (not just exif). But it DOES import certain 'portrait' photo's, but also some it does not... I will have a look at filenames, but I don't think this is the issue...
Anyone solution?

---

### Post by finite9 on 2006-10-02
Well, apologies for not 'closing' this thread, but I got it working, and the problem was purely that I hadn't chosen the right folder to import.  The file chooser is not clear and when I chose my Windows D: drive, I expect to drill down to the right directory, but not so in f-spot, it chooses the entire drive!

And this is what went wrong...for some reason, it didn't scan the *whole* drive, hence partly imported folders.  When I chose the specific main directory for my folders, then it correctly imported all my photos.

---

### Post by warjowuch on 2006-10-06
Not so for me... It does import a whole folder, but not these specifically pictures verticalized...
Wich version do you use? I have seen on my laptop that there, version 0.2 did do it, 0.1.11 does not on my desktop.

---

### Post by ttp on 2006-10-06
"f-spot cannot import images imported and automatically rotated with gnome-volume-manager-gthumb"

[https://launchpad.net/products/f-spot/+bug/37972]("https://launchpad.net/products/f-spot/+bug/37972")

This bug is fixed in Edgy.

---

### Post by jdunn on 2006-10-06
Personally, I prefer G-spot

---

