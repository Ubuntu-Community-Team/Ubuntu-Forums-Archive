---
title: "resizing photo's"
date: 2009-04-08
forum: General Help
---

### Post by LIGHTNINJIM on 2009-04-08
Hi, 
I've done a search of the forums amd a bit of googling but can't find what I'm looking for.

We recently got a 8meg camera. I've taken a few photos and downloaded them to the pc. Problem is the file sizes are huge (several Mb) and I can't post them to some places as the photo's are bigger than what they allow.

How can I cut down the photo file size without trimming the actual image and without compressing (I.E. zipping)?

Thanks in advance for any replies
Jim

EDIT:- when comparing the photos from our new camera to those of the old in a viewer they are physically almost twice the size of the old ones. Can I reduce the physical size without trimming also?

---

### Post by rudy.elgato on 2009-04-08
I use GIMP -> Image -> Scale Image to reduce the size of images.

Give that a try...

---

### Post by mdawg414 on 2009-04-08
I'm a fan of F-Spot Photo Manager myself. Just resize the image to smaller dimensions and your file size will drop

---

### Post by Therion on 2009-04-08
When Gimp is more than you need, use gThumb.  Nifty!  

And it's in the repos and Add/Remove.

[http://gthumb.sourceforge.net/features.html](http://gthumb.sourceforge.net/features.html)

---

### Post by coffeecat on 2009-04-08
You don't say whether you're running Ubuntu, Xubuntu or Kubuntu, nor which version. If you were running Jaunty Gnome you could simply right-click on an image file and choose 'Resize Images'. If you highlight several you can do a batch resize.

This is a fairly new gnome feature, so I don't know if it's available in Intrepid. Perhaps someone could check.

**Edit:** I thought I'd check for myself. No you can't do this from Intrepid. Clearly, it's a gnome 2.26 feature. **LIGHTNINJIM**, something to look forward to. In Jaunty Ubuntu you'll be able to batch resize photos without using an application - just desktop features. You can also rotate images.

---

### Post by kaibob on 2009-04-08
Phatch is another option:

[http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by LIGHTNINJIM on 2009-04-09
Thankyou all for your replies.

I should have said that i'm running Hardy LTS (noted for the future though;))

The resize function: in gimp is that under Image then Print size?
If so do I adjust the pixels or millimeters? or both?

Again, thanks for any replies

---

### Post by sekinto on 2009-04-09
If you download ImageMagick you can do batch conversion operations.
The PIL (Python Imaging Library) for Python is pretty good for this kind of stuff to.

---

### Post by mb_webguy on 2009-04-09
> **LIGHTNINJIM said:**
> Thankyou all for your replies.

I should have said that i'm running Hardy LTS (noted for the future though;))

The resize function: in gimp is that under Image then Print size?
If so do I adjust the pixels or millimeters? or both?

Again, thanks for any replies

No, in Gimp it would be Image->Scale Image.

However, as much as I love Gimp, if all you want to do is resize the images, Gimp is overkill.  It's much simpler to resize images using gThumb.

With gThumb, it's Image->Resize, which you can access with the shortcut Ctrl+S.  The reason I suggest gThumb over Gimp for this, though, is that gThumb allows you to easily switch from one image to the next in a directory, whereas in Gimp you have to open, scale, save, close, and repeat.  In gThumb, it's simply resize, save, next.

---

### Post by ryanhaigh on 2009-04-09
What you want is [nautilus-image-converter]("apt://nautilus-image-converter") which will give you the right click option and works with multiple files. For posting to places like facebook etc I would suggest using something like 1024x768 or less, if you are using flickr and want people to be able to print the photos then use a larger size.

coffeecat do you have this package installed, I wouldn't have thought gnome would be incluing this functionality inside nautilus.

---

### Post by coffeecat on 2009-04-09
> **ryanhaigh said:**
> What you want is [nautilus-image-converter]("apt://nautilus-image-converter") 

<snip>

coffeecat do you have this package installed, I wouldn't have thought gnome would be incluing this functionality inside nautilus.

Thanks for the clarification. I see from booting up the Jaunty Beta live CD that the functionality indeed is not built in, neither is nautilus-image-converter preinstalled. I must have read about it, thought it a good idea, and promptly forgotten that I had to install the package to get the function. <sigh> A symptom of advancing years, I fear. :(

Apologies to all that I've posted misleading information, but I can confirm that nautilus-image-converter is worth having. And that it's in the universe repository. Or at least it is in Jaunty.

---

