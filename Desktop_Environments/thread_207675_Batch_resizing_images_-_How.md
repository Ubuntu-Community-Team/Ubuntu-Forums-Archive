---
title: "Batch resizing images - How?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Amon_Re on 2006-07-02
Hi,

I need to resize about 70 pictures to place them on a website, but i haven't got the faintest idea what tool can do this in linux, any suggestions?

---

### Post by dpaint4 on 2006-07-02
I wonder if you could look into scripting for Gimp? Search on that topic or Google to see if people are doing it. 

Imagemagic is another thing people use to do what you're talking about realtime on their server, or locally on their machine, but I know nothing about that. I tend to do my thumbs individually because I want a lot of control over them on a case by case basis.

Just trying to give you some terms to look in to. I'm not sure Imagemagic is spelled with a 'c' at the end. It might have one of those stupid 'ends with a k for no reason' spellings.

---

### Post by Amon_Re on 2006-07-02
[QUOTE=dpaint4]I wonder if you could look into scripting for Gimp? Search on that topic or Google to see if people are doing it. 

Imagemagic is another thing people use to do what you're talking about realtime on their server, or locally on their machine, but I know nothing about that. I tend to do my thumbs individually because I want a lot of control over them on a case by case basis.

Just trying to give you some terms to look in to. I'm not sure Imagemagic is spelled with a 'c' at the end. It might have one of those stupid 'ends with a k for no reason' spellings.[/QUOTE]

Don't get me wrong, but i'm not about to start learning python just to resize afew silly pictures, might be better of installing wine then.

You're refurring to Image Magick, might have to take a closer look at that one

Edit: [http://www.novell.com/coolsolutions/tip/16524.html](http://www.novell.com/coolsolutions/tip/16524.html)

---

### Post by Paqman on 2007-09-27
You can indeed [resize batches of images with GIMP](http://www.math.tu-berlin.de/~choumili/batch_resize.php)

---

### Post by mcduck on 2007-09-27
Imagemagick is possibly the best & most powerful tool for handling large amounts of images.

[http://www.imagemagick.org/]("http://www.imagemagick.org/")

I use it quite often when I need to compress hundreds of images and make thumbnails for them. Type the command needed, push enter and go make yourself a nice cup of coffee while your computer is doing the work for you. :D

For example the following command would resize all .jpg images in a directory to 640x480, with quality setting 86 (you can choose between 0 and 100) and strip EXIF data from them to make files even smaller:
```

find . -iname "*.jpg" -exec convert -resize 640x480 -quality 86 -strip {};
```

There's actually a nice Nautilus extension (that uses Imagemagick) in Ubuntu repositories that allows you to just select all images you want to resize, right-click, select 'Resize Images' and choose the size you want from a GUI menu. To get it run the following command and log out &back again (or 'killall nautilus'):
```
sudo apt-get install nautilus-image-converter
```

---

### Post by Paqman on 2007-10-02
> **mcduck said:**
> 
There's actually a nice Nautilus extension (that uses Imagemagick) in Ubuntu repositories that allows you to just select all images you want to resize, right-click, select 'Resize Images' and choose the size you want from a GUI menu. To get it run the following command and log out &back again (or 'killall nautilus'):


I'd been wanting something like that for ages, thanks for the tip!

---

### Post by unprinted on 2007-10-09
ImageMagick did the job for me, thank you, but it's got a surprisingly large learning curve.

I could do one image ok - once I got used to the idea that you need to say 'pretty please' when resizing something and it will make it smaller - but I needed to use someone else's recipe to do more than one at a time...

---

### Post by stani on 2007-10-13
I just created a program for this: phatch = photo & batch!

For more info see: [http://photobatch.stani.be](http://photobatch.stani.be)

---

### Post by ozzyprv on 2007-11-07
Thank you Stani, your program worked for me!.

---

### Post by stani on 2007-11-10
It is my pleasure ;-)

---

### Post by Robbyx on 2007-11-26
I have just installed image magick and the nautilus extension. 

I can not see the extension in Nautlilus. Where should I look? I have tried right clicking a jpg file but nothing about image magick is showing.

Robin
Using Fiesty

---

### Post by mcduck on 2007-11-26
> **Robbyx said:**
> I have just installed image magick and the nautilus extension. 

I can not see the extension in Nautlilus. Where should I look? I have tried right clicking a jpg file but nothing about image magick is showing.

Robin
Using Fiesty

You need to either restart Nautilus or log out and back again. Then when right-clicking image(s) near the bottom of the menu are options 'Resize Images..' and 'Rotate Images..'.

---

### Post by Robbyx on 2007-11-26
Thank you. I now see it.

---

### Post by Robbyx on 2007-11-26
find . -iname "*.jpg" -exec convert -resize 640x480 -quality 86 -strip {};

It seems that the N addon does not offer most of your command line options. Is there another program that offers that? I ask because I find command line options difficult to recall if I am not using them often, therefore a front end is a useful aid. In this case it mises out some of the options.

Robin

---

### Post by Robbyx on 2007-12-01
Does anyone know of any other front ends that are available, with a fuller range of commands?

---

### Post by Robbyx on 2007-12-01
Alternatively is there a way of attaching a command line to a desktop  icon, so that everytime the icon is pressed the full command line is run, rather like a batch file?

---

### Post by samwyse on 2007-12-01
Use Gwenview (KDE).

---

### Post by Robbyx on 2007-12-01
Thanks for the recommendation

R

---

### Post by stani on 2007-12-05
> **Robbyx said:**
> Does anyone know of any other front ends that are available, with a fuller range of commands?

Hi Robbyx, did you try phatch?

---

### Post by Robbyx on 2007-12-05
Can you suggest how I use it?

I seem to be opening an unsaved action list. How do I get it to open a jpg?


> **stani said:**
> Hi Robbyx, did you try phatch?

---

### Post by stani on 2007-12-05
> **Robbyx said:**
> Can you suggest how I use it?

I seem to be opening an unsaved action list. How do I get it to open a jpg?

Action lists are used to describe how photos should be batch processed. There is no option to open  or preview your changes. (The processed photos will be saved in a copy folder.) There is no manual yet, but some people started blogging about or reviewing phatch with instructions:
[http://jcornuz.wordpress.com/2007/11...t-bash-hassle/](http://jcornuz.wordpress.com/2007/11...t-bash-hassle/)
[http://www.softpedia.com/reviews/lin...ew-71656.shtml](http://www.softpedia.com/reviews/lin...ew-71656.shtml)

For more info, see also:
[http://ubuntuforums.org/showthread.php?t=466598&highlight=phatch](http://ubuntuforums.org/showthread.php?t=466598&highlight=phatch)

Phatch is easy if you have to process thousands of photos in a certain way, but is not an 'individual photo' editor.

---

### Post by scaine on 2008-03-15
Hi Stani,
Perhaps this is covered in your support forums and I will check there shortly, however, when I run Phatch (excellent interface btw), it does everything I want EXCEPT retain my Exif info, such as which camera I used, exposure, etc.

Is there any way to have Phatch do this?  I haven't found a better program for batch image processing, but if it can't retain the Exif info, I'm back to using Windows tools, such as Easy Thumbnail under Wine.

---

### Post by stani on 2008-03-16
> **scaine said:**
> Hi Stani,
Perhaps this is covered in your support forums and I will check there shortly, however, when I run Phatch (excellent interface btw), it does everything I want EXCEPT retain my Exif info, such as which camera I used, exposure, etc.

Is there any way to have Phatch do this?  I haven't found a better program for batch image processing, but if it can't retain the Exif info, I'm back to using Windows tools, such as Easy Thumbnail under Wine.
Haha, lazy scaine,
You didn't take the effort to read:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598) :
> * If you want improved exif support, please download this installer. 
So download and install this (for hardy, but works on gutsy):
[http://packages.ubuntu.com/hardy/python/python-pyexiv2](http://packages.ubuntu.com/hardy/python/python-pyexiv2)

In Hardy this will be solved automatically.

Stani

---

### Post by scaine on 2008-03-16
> **stani said:**
> Haha, lazy scaine,
You didn't take the effort to read:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598) :


:) Yep - totally guilty!  I've tried so many of these tools now that I'm just skimming them now and I came across your program from a google search!  ("jpg batch convert" if I remember correctly.

This is awesome news, Stani.  I'll try this installer tonight.  I'm happy to say it again though - if your installer fixes the EXIF bug I ran into, then your Phatch tool is by far the best program I've ever experienced for this type of work.

Thanks.

---

### Post by scaine on 2008-03-16
Ach - damn.  I already had python-pyexiv2 installed.  I also downloaded every tool that Synaptic returned with "exif" as a search - no dice.  Even after a reboot (worth a shot :))

The command line tool "Exif2" shows all the information, as does Nautilus and EOG, but for some reason, Phatch doesn't appear to see any Exif at all.  It must be python related, but I'm at a total loss to explain it.

Any suggestions would be gratefully welcomed.  I'm running Hardy on this machine, btw.  I'll try the same install on my Eee which is running Gutsy.  It's worth a shot.

If you give me details on how to do so, I'll log a launchpad bug for this, Stani.
[EDIT : I've created a bug on the launchpad entry for Phatch]

Oh, I also regressed to the Phatch version from the Hardy repos, but it has the same issue as the deb file I downloaded from your site.

Thanks.

---

### Post by stani on 2008-03-16
Did you check "Save Metadata (exif & iptc)" in the execute dialog?

---

### Post by scaine on 2008-03-17
Just to report in this thread that Stani is working away on [the launchpad bug I raised]("https://bugs.launchpad.net/phatch/+bug/202989") and has already released a new version of the code which is a giant step towards fixing this Exif issue.

Magic work, mate and thanks for the time you're putting into this (not to mention the time put into creating Phatch in the first place...)!

=D>

---

### Post by juky on 2008-04-06
Hi all

I am  using version 0.1.bzr496, but after batch rotate, image does not show exif data. Anyone else had this issue on this version?

---

### Post by juky on 2008-04-06
> **mcduck said:**
> Imagemagick is possibly the best & most powerful tool for handling large amounts of images.

[http://www.imagemagick.org/]("http://www.imagemagick.org/")

I use it quite often when I need to compress hundreds of images and make thumbnails for them. Type the command needed, push enter and go make yourself a nice cup of coffee while your computer is doing the work for you. :D

For example the following command would resize all .jpg images in a directory to 640x480, with quality setting 86 (you can choose between 0 and 100) and strip EXIF data from them to make files even smaller:
```

find . -iname "*.jpg" -exec convert -resize 640x480 -quality 86 -strip {};
```

There's actually a nice Nautilus extension (that uses Imagemagick) in Ubuntu repositories that allows you to just select all images you want to resize, right-click, select 'Resize Images' and choose the size you want from a GUI menu. To get it run the following command and log out &back again (or 'killall nautilus'):
```
sudo apt-get install nautilus-image-converter
```

This works, but the exif data is removed from image. Any idea how to keep exif?

---

### Post by mcduck on 2008-04-06
> **juky said:**
> This works, but the exif data is removed from image. Any idea how to keep exif?

Just leave the "-strip" option from the command and your EXIF data will not be removed.

"-strip" is used to remove EXIF data from images to get even smaller file sizes.

---

### Post by juky on 2008-04-07
@ mcduck:

Actually, I am rotating images through nautilus, and then exif data is lost. 

Through terminal, although I removed -strip option, exif data is still removed.

But I have found nice scripts that does the job.

Take a look at:

[http://www.movingtofreedom.org/2007/10/28/how-to-rotate-jpg-images-in-gnome-nautilus-file-manager/](http://www.movingtofreedom.org/2007/10/28/how-to-rotate-jpg-images-in-gnome-nautilus-file-manager/)

It worked a charm for me.

Thanks anyhow.

Cheers
juky

---

### Post by runemaste644 on 2008-04-07
To resize in a batch
(lets say your images are png files in ~/myimages and we are resizing it to 1024x768)
```
$ cd $HOME/myimages
$ mkdir small
$ convert -resize 1024x768 `ls *.png` small/sm-*.png
```

---

