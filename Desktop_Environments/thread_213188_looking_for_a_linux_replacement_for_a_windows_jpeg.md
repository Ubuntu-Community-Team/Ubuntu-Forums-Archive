---
title: "looking for a linux replacement for a windows jpeg (lossless) compressor / cleaner"
date: 2006-07-11
forum: Desktop Environments
---

### Post by ewaguespack on 2006-07-11
I am pretty much converted completely to linux, but there are still a couple of programs that I have not found a replacement for, below is the feature list... if a program does not currently exist, I wonder if imagemagic or perl or both would be the right tools to hack something together?


thanks in advance.




[http://www.davidcrowell.com/jStrip/Default.aspx](http://www.davidcrowell.com/jStrip/Default.aspx)

jStrip is a free tool to reduce the file size of JPEG images without sacrificing image quality. High-traffic websites with many JPEG images can benefit from decreased bandwidth costs. Less hard disk space will be used by image collectors.

jStrip works by removing unneeded data from JPEG files. This data is unused by web browsers and image viewing software. jStrip does not re-compress an image, so there is no image quality loss.
Features

jStrip removes the following from JPEG files:

* Comments (optionally)
* EXIF Data (optionally)
* JFIF Header (optionally)
* Photoshop Image Resource Block (optionally)
* ICC color profile
* Adobe APP14 tag (optionally)
* XMP data (optionally)
* Extra bytes at end of file
* Extra bytes or header at beginning of file
* Extra bytes between JPEG blocks
* Application-specific APPx blocks
* Photoshop thumbnails
* Any other unknown blocks in the JPEG files

jStrip also has the following features:

* Option to retain original time-stamp of modified files
* Ability to process a single file, or batch processing, including recursing a folder tree
* Option to attempt to clear read-only bit
* Includes a full help file
* Allows browsing and processing of UNC paths
* A command line version for batch processing
* Can change case of filenames, and change %20 and underscores to spaces in filenames

Supported Operating Systems

* Windows 95 with Internet Explorer 4
* Windows NT4 with Service Pack 6a and Internet Explorer 4
* Windows 98
* Windows 2000 Professional or Server
* Windows ME
* Windows XP Home or Professional
* Windows Server 2003

---

### Post by aysiu on 2006-07-11
Have you tried *mogrify*? ```
mogrify -resize 200x200 *.jpg
``` Or you may want to check this out:
[http://www.cit.gu.edu.au/~anthony/graphics/imagick6/formats/#jpg_non_im](http://www.cit.gu.edu.au/~anthony/graphics/imagick6/formats/#jpg_non_im)

---

### Post by eloj on 2006-07-11
See if exiv2 can do the job for you. The [manual](http://www.die.net/doc/linux/man/man1/exiv2.1.html) suggest that it could. It'll remove metadata for you, but it might not remove padding from the header and such.

---

### Post by ewaguespack on 2006-10-03
well I finally found some solutions:

find -type f -iname "*.jpg" -exec jpegtrans -progressive -outfile {} {} \;

its actually an improvement over jstrip, it results in a smaller file, the only thing that I can tell that jpegtrans fails to strip is the jfif header, which is only 18 bytes.

yay... that's basically the last bit of software that was locking me  into windows xp.

well I guess I should try out k3b before I say that...

---

