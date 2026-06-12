---
title: "[SOLVED] Set as desktop background fails"
date: 2008-12-28
forum: General Help
---

### Post by skern03 on 2008-12-28
If you right-click on a web image, like the one here:
[http://apod.nasa.gov/apod/](http://apod.nasa.gov/apod/)
the context menu has an option to set the image as the desktop background. If you select the option, you get a small window displaying the image with options to stretch, center or tile. 

However, it seems to only work once. Subsequent attempts fail. The image isn't loaded (see attached screenshot) into the monitor image - it's just gray. If you change the option from stretch to center and back, the image appears. However, clicking the Set Desktop Background button does absolutely nothing.

This happens every time I've installed Ubuntu.

I wish Ubuntu had the desktop background chooser that Kubuntu has....

And yeah, I like eye candy ;-)

---

### Post by Wartender on 2008-12-28
why don't you try setting it by right-clicking the desktop and selecting "change desktop background" and use your image from there?

---

### Post by skern03 on 2008-12-28
Thanks for the reply. I tried that before posting. Unfortunately, you have to save the image first, which kinda defeats the purpose of having the Set as desktop background option for images. 

I also tried putting the url directly in the search bar, for example:
[http://apod.nasa.gov/apod/image/0812/thackeray_hst_big.jpg](http://apod.nasa.gov/apod/image/0812/thackeray_hst_big.jpg)
It just clocks and never loads anything.

> **Wartender said:**
> why don't you try setting it by right-clicking the desktop and selecting "change desktop background" and use your image from there?

---

### Post by gettinoriginal on 2008-12-28
Instead of "set as desktop", use "save image as", save it to pictures, then just drag and drop it into your Appearance > Background images.  It does work, as I just tried it.  :P

---

### Post by skern03 on 2008-12-28
Thanks for the work-around! I like the drag-n-drop functionality.

Still, I'd like to see the context menu item functional. IMHO, it's a bug.

> **gettinoriginal said:**
> Instead of "set as desktop", use "save image as", save it to pictures, then just drag and drop it into your Appearance > Background images.  It does work, as I just tried it.  :P

---

### Post by gettinoriginal on 2008-12-28
Glad it worked, please go to tools and mark this as solved :P

---

### Post by steveneddy on 2008-12-28
> **skern03 said:**
> Thanks for the work-around! I like the drag-n-drop functionality.

Still, I'd like to see the context menu item functional. IMHO, it's a bug.

Then please file a bug report on Launchpad.

And if you feel this thread is solved, please mark it as so.

---

### Post by skern03 on 2008-12-28
On Launchpad, there is a bug report that is marked resolved, released last November. However, the bug is still clearly present, so I submitted a new bug report. It appears there's nothing but the work-arounds mentioned above.

I'll mark the top post.

---

### Post by steveneddy on 2008-12-28
> **skern03 said:**
> On Launchpad, there is a bug report that is marked resolved, released last November. However, the bug is still clearly present, so I submitted a new bug report. It appears there's nothing but the work-arounds mentioned above.

I'll mark the top post.

I believe that you can go to the top of the thread to "Thread Tools" and select "Mark as Solved"

BTW - it doesn't work for me either. Then again, I always save the pic to a file and use that for a wallpaper.

---

### Post by skern03 on 2008-12-28
> **steveneddy said:**
> I believe that you can go to the top of the thread to "Thread Tools" and select "Mark as Solved" 

Already did that earlier today, but apparently it didn't take. I've had sporadic Firefox issues today, so maybe it didn't post. I tried again, and this time it worked. Thanks for letting me know!

---

### Post by skern03 on 2008-12-28
I received the following response from launchpad:

> *** This bug is a duplicate of bug 206191 ***
    [https://bugs.launchpad.net/bugs/206191](https://bugs.launchpad.net/bugs/206191)

It is marked as fixed in Intrepid, but still has a task open for Hardy


Unfortunately, I can't run Intrepid on my system.:(

---

### Post by steveneddy on 2009-01-08
I read recently that installing the package

**nautilus-wallpaper**

will solve the issue of the original poster.

I will try this at home tonight so see if it works for me, too.

---

### Post by steveneddy on 2009-01-08
I can confirm that installing the package

**nautilus-wallpaper**

makes Gnome add a wallpaper from the internet, as long as it is the correct file format.

```
sudo apt-get nautilus-wallpaper
```

---

