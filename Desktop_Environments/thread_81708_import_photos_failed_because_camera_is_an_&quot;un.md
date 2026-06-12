---
title: "import photos failed because camera is an &quot;unknown model&quot;"
date: 2005-10-25
forum: Desktop Environments
---

### Post by evan1221 on 2005-10-25
Hi,

I have a digital camera (model Casio QVR4), which I connected with an USB cable to my computer.

A window appeared asking me if I wanted to import photos in my library. I clicked "Import Photos". Gthumb opened, but did not import my photos. So I opened the menu "File" in Gthumb, and clicked "Import Photos". An error window told me "Could not import photos. Unknown model".

My question is, what is the point of knowing the camera model if the camera is already auto-mounted on the filesystem (under "/media/SANVOL" in my case)? Is there any way to tell gthumb to simply get the photos from the mounted point?

Of course, it is possible to copy the files using nautilus, but then we lose the point of having a nice piece software that takes care of our photos for us...

Thanks,

Evan

---

### Post by not_yet on 2005-10-25
I may be off base here, but I think you need gtkam to move the pics from your camera first, then gthumb should be able to display them from your hard drive.

or do you already have gtkam installed?

---

### Post by evan1221 on 2005-10-27
Oh I didn't know gtkram. I installed it but it uses the same library as gthumb, namely gphoto2. So the result was the same.

Does anybody know about an automatic photo import function for cameras that act as usb mass storage devices?

---

### Post by markmark on 2005-10-30
[QUOTE=evan1221]Does anybody know about an automatic photo import function for cameras that act as usb mass storage devices?[/QUOTE]I've been playing with the photo importer [here]("http://www.grawert.net/software/pimp/") today, and it seems to do the job. The only thing was it only searched on *.jpg and was missing the files on my camera which are named as .JPG. I fixed that by changing the line:
my @piclist = `find $ARGV[0] -name '*.jpg'`;
in /usr/bin/pimp to read:
my @piclist = `find $ARGV[0] -iname '*.jpg'`;
This makes it case insensitive.

---

### Post by evan1221 on 2005-10-30
Oh this one looks quite neat !! I will try it :)

Thanks ^^

---

### Post by Eremit on 2005-11-01
Adding the user to group "**plugdev**" solved the problem for me

---

### Post by Chris Tucker on 2005-12-15
> **markmark]I've been playing with the photo importer [here]("http://www.grawert.net/software/pimp/") today, and it seems to do the job. The only thing was it only searched on *.jpg and was missing the files on my camera which are named as .JPG. I fixed that by changing the line:
my @piclist = `find $ARGV[0] -name '*.jpg'` said:**
>  -iname '*.jpg'`;
This makes it case insensitive.
any way to make it import MPG movies?

---

