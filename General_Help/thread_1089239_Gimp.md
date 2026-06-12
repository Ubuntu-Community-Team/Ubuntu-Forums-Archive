---
title: "Gimp"
date: 2009-03-06
forum: General Help
---

### Post by jwkungfu on 2009-03-06
Hi all, 

I would like to alter a picture, save it, so that I can then upload it to a website (in JPEG, PNG, TIFF, BMP, or GIF format)...
I opened a picture Places/Pictures....
Altered it, but couldn't save it as a in JPEG, PNG, TIFF, BMP, or GIF...

Any suggestions?

Which format is best for Ubuntu users? (eg. audio files .flac is better than .mp3... I've been told?)

Is the editing package (default when opening a picture from the Ubuntu toolbar) GIMP...?
In the package manager it appears that I have it installed? Although it's not listed under Applications....?

Thanks in advance!!
LINUX is THE ONLY "CHOICE"!!!!!!!!!!!!!!

jw.

---

### Post by martrn on 2009-03-06
> I opened a picture Places/Pictures....  Altered it, but couldn't save it as a in JPEG, PNG, TIFF, BMP, or GIF...  Any suggestions?

This could be one of two (or more) things.

1.  You could be trying to save a jpeg, png, tiff, bmp or gif file to a write protected drive or directory.  Try saving the file to /home/yourname/Desktop  to see if you can save the file to your desktop, if you can then you need to make sure you have read/write assess to the directory where you wish to save the file to.

2.  You have unmet dependencies with the 'gimp - gnu image manipulation program'.  Try ```
sudo apt-get -f install gimp
``` to install the gimp and all its dependencies.

---

### Post by jwkungfu on 2009-03-07
Thanks for the reply!

The problem isn't actually saving the file (I was saving it to the desktop as.odf), but it was with selecting a format such as GIF, JPEG, etc...

The website that I'm hoping to upload the picture to requires files to be in JPEG, PNG, TIFF, BMP, or GIF

I did the sudo command in a terminal as you suggested and it came back saying that I already have the current version, so nothing was updated/changed... How come GIMP isn't listed in any of my Applications?

---

### Post by cotcot on 2009-03-07
We need some clarification.
What is the type of picture you open ? 

What means Places/Pictures ? I do not see this menu entry in gimp. From you guestion if Gimp is the default for opening pictures I am not sure that you are in gimp if you open the image. So look in Application under Graphics and start gimp from there.

.flac is sometimes recommended instead of .mp3 because it is a lossless and free codec. 
For images .png is also free and lossless and free. The filesize is larger than jpeg.

---

### Post by 3rdalbum on 2009-03-07
Depending on your Gnome settings, it might just be listed as "Image Editor".

You can run The Gimp in a terminal:

```
gimp
```

Or, instead of double-clicking the file you want to convert, right-click and choose "Open With" and The Gimp should be on the list.

---

### Post by martrn on 2009-03-07
You could check you have all the dependencies installed :

```
sudo apt-get install gimp-data libaa1 libart-2.0-2 libatk1.0-0 libc6 libcairo2 libdbus-1-3 libdbus-glib-1-2 libexif12 libfontconfig1  libfreetype6 libgimp2.0 libglib2.0-0 libgtk2.0-0 libgtkhtml2-0 libhal1  libjpeg62 liblcms1 libmng1 libpango1.0-0 libpng12-0 libpoppler-glib2 librsvg2-2 libtiff4 libwmf0.2-7 libx11-6 libxext6 libxmu6 libxpm4 zlib1g gimp-gnomevfs gimp-python 
```

Alternatively you could uninstall and re-istall :

```
sudo apt-get remove --purge gimp
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install gimp
```

It doesn't sound like it has installed properly.

---

