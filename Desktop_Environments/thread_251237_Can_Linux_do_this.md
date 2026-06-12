---
title: "Can Linux do this?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by salmankhilji on 2006-09-05
I have video files that I'd like to make previews of.  On Windows, there is a software available called Image Grabber which does this.  I am attaching two image files---one is a screenshot of Image Grabber showing you the kind of options that I am looking for.  The second one is the kind out output that I'd like to produce.

I am sure this can be done with xine and some gimp scripts, but I'd like to know how.

Salman

---

### Post by H.E. Pennypacker on 2007-01-07
This is exactly what I am looking for...anyone know the answer?

---

### Post by tagra123 on 2007-01-07
ffmpeg  should do it.

ffmpeg -y -i [videofile] -vframes 1 -ss 00:00:02 -an -vcodec png -f rawvideo -s 320X240 [thumbnailimage.png]

Above in the size -s 320X240  make sure the X is uppercase or you will receive a size error.

---

### Post by linuchsan on 2007-01-08
or you can use gimageview

---

### Post by H.E. Pennypacker on 2007-01-08
> **tagra123 said:**
> ffmpeg  should do it.

ffmpeg -y -i [videofile] -vframes 1 -ss 00:00:02 -an -vcodec png -f rawvideo -s 320X240 [thumbnailimage.png]

Above in the size -s 320X240  make sure the X is uppercase or you will receive a size error.

ImageGrabber takes all those screenshots and puts them in one image file, in addition to the file information.  Examples of ImageGrabber output is in the original poster's post.

---

### Post by orb9220 on 2007-01-08
For images it is known as making a contact sheet. And there are a few graphic programs that does that.

Gthumb 2.7.9 does that but it is called Create Index Image under tools. you multi-select the images then select Create Index Image under tools,

Just made one with 4 images so it works.

---

### Post by cx23 on 2007-06-13
Try this:

[http://sourceforge.net/projects/slickslice/](http://sourceforge.net/projects/slickslice/)

SlickSlice is a bash script powered by ImageMagick and Mplayer tools that creates a timeline representation of a videofile - one big image with screenshot thumbnails taken at automatically set periods of time.

[[IMG]http://img253.imageshack.us/img253/7540/slickslicedplan9fromoutxx6.jpg[/IMG]](http://imageshack.us)

---

### Post by rjbgbo on 2008-02-22
Very good

Script Sequential Video Thumbnails on Linux

[http://tobyinkster.co.uk/blog/2007/08/19/dhyana/](http://tobyinkster.co.uk/blog/2007/08/19/dhyana/)

To install in nautilus scripts

```
/home/USER/.gnome2/nautilus-scripts
```

Make the file executable by right clicking it, selecting "Properties", "Permissions" tab, then check the box next to "Execute"

---

