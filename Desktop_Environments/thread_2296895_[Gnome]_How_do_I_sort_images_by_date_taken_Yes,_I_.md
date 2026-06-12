---
title: "[Gnome] How do I sort images by date taken? Yes, I could boot Windows and do it ..."
date: 2015-09-29
forum: Desktop Environments
---

### Post by Olotila on 2015-09-29
... but I prefer Linux.

When I copy images from my phone to PC, the date changes to time of the copying. How do I sort images so, that I can select them by which month they were taken?

---

### Post by TheFu on 2015-09-30
My images usually have either a timestamp in the filename or a sequence number in the filename which if sorted alphabetically will keep the order that the photos were taken.

If that is NOT the situation, you'll need to use the exif data.  Check the dates using something like exiftool.  Or you can load shotwell (or the 10 other photo management tools for Linux) and let them do this for you. f-spot, 
[http://itsfoss.com/image-applications-ubuntu-linux/](http://itsfoss.com/image-applications-ubuntu-linux/) has some.
[http://lifehacker.com/5877908/the-best-photo-management-app-for-linux](http://lifehacker.com/5877908/the-best-photo-management-app-for-linux) has some more options.

I just let my photo web-app handle it.

---

### Post by buzzingrobot on 2015-09-30
Any chance the camera settings can be adjusted to put a timestamp in the filenames it creates? 

Default filenames coming out of cameras tend to be pretty useless, in my experience.

---

### Post by QDR06VV9 on 2015-09-30
And there is always View by Modification Date.

---

### Post by TheFu on 2015-09-30
```
exiftool *jpg|grep -Ei 'Original|File Name'
```

So it wouldn't be too hard to rename the existing filenames to have the yyyymmdd-hhmmss-original_filename.ext.

Just sayin'.

Plus it is a *best practice* to store photos in yyyy/mm/event/ directory structures, so the photos will always be within a day if they are in the same directory.  Nothing matters more than the date of a photo for most people. Followed by location and subjects.

---

### Post by buzzingrobot on 2015-10-01
> **TheFu said:**
> ```
exiftool *jpg|grep -Ei 'Original|File Name'
```



I will use that. :p 

I'm lazily working out a lazy person's workflow that avoids app-specific catalogs, tags, and such. A filename can be used to contain a lot of info if you devise a useful format and discipline yourself to adhere to it.

---

### Post by TheFu on 2015-10-01
[http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival) - step 6 is the gist of what I do.

---

### Post by buzzingrobot on 2015-10-01
Thanks.  Appreciate that.

---

### Post by QDR06VV9 on 2015-10-01
> **TheFu said:**
> [http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival) - step 6 is the gist of what I do.
This certainly makes the most sense!
Thanks for the detailed link much [COLOR=#000000]Appreciated.[/COLOR];)

---

### Post by Olotila on 2015-10-02
> **buzzingrobot said:**
> Any chance the camera settings can be adjusted to put a timestamp in the filenames it creates? 



Pics and videos taken by different devices, also screenshots etc. I also want to handle old pictures sometimes, so this does not help.

> **runrickus said:**
> And there is always View by Modification Date.

Modification date is the time, when I moved the pics from camera to PC, not time when picture taken.

Thanks guys for the other options, I'm looking those up. Also looking for a way to integrate exif data to say Nautilus, or some other filemanager.

---

### Post by TheFu on 2015-10-02
[https://askubuntu.com/questions/33359/app-for-viewing-photos-with-properties-exif-display](https://askubuntu.com/questions/33359/app-for-viewing-photos-with-properties-exif-display) says that nautilus can do this. I don't use file managers, so don't know if/how that works.

---

### Post by Olotila on 2015-10-02
Any opinions about this?

[http://www.webupd8.org/2010/10/music-and-exif-metadata-information-in.html](http://www.webupd8.org/2010/10/music-and-exif-metadata-information-in.html)

---

### Post by TheFu on 2015-10-02
> **Olotila said:**
> Any opinions about this?

[http://www.webupd8.org/2010/10/music-and-exif-metadata-information-in.html](http://www.webupd8.org/2010/10/music-and-exif-metadata-information-in.html)

It is 5 yrs old and ran on basically, marginally different OSes than what we are running today.
If you do try it, be certain you have excellent backups for anything you cannot do without and when I say that, I mean
* the entire OS - if you can do without it - don't back it up.
* the OS settings - usually /etc/
* Personal settings - basically your HOME.

Good luck.

---

### Post by Olotila on 2015-10-07
Well, I could not trust the 5 years old software, so I booted to Windows and was done with the task in 5 minutes. Maybe I will use gThumb or similar in the future, but now I go with non-networked Windows. Sad but true.

---

### Post by TheFu on 2015-10-07
> **Olotila said:**
> Well, I could not trust the 5 years old software, so I booted to Windows and was done with the task in 5 minutes. Maybe I will use gThumb or similar in the future, but now I go with non-networked Windows. Sad but true.

Doesn't Windows accomplish this by creating temporary files somewhere that never get cleaned up? XMP-something?

---

### Post by Olotila on 2015-10-08
Well, I dont trust windows at all anymore, so I was offline when logged in and cleaned temp folders before logging out.

---

