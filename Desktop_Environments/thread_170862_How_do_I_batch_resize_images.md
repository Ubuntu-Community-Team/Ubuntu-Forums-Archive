---
title: "How do I batch resize images?"
date: 2006-05-05
forum: Desktop Environments
---

### Post by Gobd on 2006-05-05
Is there a single program for Linux that can batch resize images that doesn't require me to do everything in the command line or compile a plugin? Through all my searching all I have found are things that are only command line or things no in the repository that I would ahve to compile. I have about 30 images I need to resize and save as jpg but I'm finding it impossible to do without my Windows install.

---

### Post by megamania on 2006-05-05
[QUOTE=Gobd]Is there a single program for Linux that can batch resize images [/QUOTE]
I'm not sure that's what you're looking for, but try Gthumb (pre-installed in ubuntu):

select the images, then Tools - Resize Images.

---

### Post by Gobd on 2006-05-05
Yeah I just found that but you can only resize one image at a time and it takes quite a bit of work. I was looking for a program like irfanview for Windows where you put in settings once, select a folder, and it resizes all images in the folder and saves them after that.

*edit* Gthumb does work with a bit more looking around. Not perfect but it will work this time.

---

### Post by ajgreeny on 2006-05-05
I've not done it but, Digikam looks as though it will batch edit, including resize all, or selected images in a folder.  You can get Digikam in the repos without a problem, and I presume it will still work even if you do not use KDE as your desktop.

Give it a try and let us know how well it does the job.

Just out of interest it's now about 10 minutes later, and I have now done exactly what I said I had not done before, and it worked very well, reducing sizes by half in both dimensions, with the opportunity to add images and then save them to wherever you wish, even a new folder if you want.

Digikam is great, much like Irfan View and Picasa put together so definitely worth a try

---

### Post by auburn on 2006-05-05
Here are some frontends (gui's) for imagemagick, the industry-standard app for such tasks:

[http://www.imagemagick.org/script/api.php](http://www.imagemagick.org/script/api.php)

(digicam is a frontend for imagemagick)

If you'd like to try the commandline, the app is already installed, simply type:

  ```
convert rose.jpg -resize 50% rose.png
```

or you can subsitute (eg) 640x480 for the 50%.

That will convert from jpg to png and resize it accordingly.

Here's where I got that example (with lots of other cool options)
[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

---

### Post by Westerberg on 2006-05-05
David's Batch Processor plug-in for GIMP will do the trick. It can batch resize, rename, blur, color, crop, and sharpen.  It has a GUI similar to Irfanview's.  To install, You will need g++, gimptool, and the gimp-devel packages. 
[http://members.ozemail.com.au/~hodsond/dbp.html](http://members.ozemail.com.au/~hodsond/dbp.html)
If the newer versions don't install, try the oldest version.

---

### Post by sveikotajs on 2007-07-02
it's not ***"gimp-devel"*** you need but ***"libgimp-2.0-dev"*** instead. Make sure you have ***build-essentials*** installed as well. Then untar the DBP download, switch to it, run ***"make"*** and ***"make install"***, if no errors you're good to go, check under Xtns in GIMP, there should be an entry for Batch Process .

I did the make etc as myself, so the plugins get installed to my home directory, but I'm the only user on this laptop. I assume if you want it system wide you'll need to do it as root.


Cheers, it's a powerful tool, worth getting installed and working



ED

---

### Post by stani on 2007-07-03
> **Gobd said:**
> Is there a single program for Linux that can batch resize images that doesn't require me to do everything in the command line or compile a plugin? 

Phatch will take care of batching your images. I can provide you a deb installer, so you only have to double click to install it. Read more here:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

If you are interested, reply on that thread.

Stani

---

### Post by kjur on 2007-07-03
It is actually a trick using line command, but pretty easy. I found it somewhere in the net. Can't remember the author of the original post.
```
for i in `ls`; do convert -resize 800x800 -quality 65 $i resized_$i; done
```

---

### Post by Skidpad on 2007-07-16
Here is a great little add-on: [Nautilus Image Converter]("http://www.getdeb.net/release.php?id=221").  It puts a "Resize Images" in your right-click menu, just like the XP Powertoy does.  It ***will*** do batch conversions too!  It isn't in the repos...gotta do the .deb download.

:)

---

### Post by mrwtr on 2007-11-12
> **Gobd said:**
> Yeah I just found that but you can only resize one image at a time and it takes quite a bit of work. I was looking for a program like irfanview for Windows where you put in settings once, select a folder, and it resizes all images in the folder and saves them after that.

*edit* Gthumb does work with a bit more looking around. Not perfect but it will work this time.

This is not true (at least for Gutsy).  Just open images in gThumb, select all images you want scaled (a.k.a. resized)  then Tools->Scale Images.

---

### Post by samwyse on 2007-11-12
Gwenview has a batch resizer also (KDE).

---

### Post by pienose on 2007-12-28
> **auburn said:**
> 

If you'd like to try the commandline, the app is already installed, simply type:

  ```
convert rose.jpg -resize 50% rose.png
```

or you can subsitute (eg) 640x480 for the 50%.

That will convert from jpg to png and resize it accordingly.

Here's where I got that example (with lots of other cool options)
[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

that works briliantly, but how could I get it to do subfolders too?

---

### Post by varanasi on 2007-12-28
Rewrite this a bit?

[http://denverhughes.net/Scripts/index.htm](http://denverhughes.net/Scripts/index.htm)

---

### Post by pienose on 2007-12-28
that could work but I'm afraid I wouln't have an idea about how to do it :(

---

### Post by stani on 2007-12-29
> **pienose said:**
> that works briliantly, but how could I get it to do subfolders too?

Phatch handles subfolders (just click on "include subfolders") easily.

[http://photobatch.stani.be](http://photobatch.stani.be)

Stani

---

### Post by xamox on 2008-01-15
> **megamania said:**
> I'm not sure that's what you're looking for, but try Gthumb (pre-installed in ubuntu):

select the images, then Tools - Resize Images.


Thanks this is what I was looking for.

---

### Post by Samhain13 on 2008-01-15
+1 for Phatch. :)

---

