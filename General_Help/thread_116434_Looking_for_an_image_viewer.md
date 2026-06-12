---
title: "Looking for an image viewer"
date: 2006-01-12
forum: General Help
---

### Post by SteveF on 2006-01-12
I take digital images which (as most point and shoots do) shoot at a 4:3 ratio.  I have them printed at 4x6 inches.  Some images do not look good cropped to 4x6 inches where the cropping occurs evenly on both sides.

I'm using imagemagick to downsize the images to 4x6 (and a little unsharp applied), but I don't want to take the time to do that for images that won't look good.  So I'm looking for a viewer which will allow me to set an aspect ratio and view all images cropped to that ratio.  I could then look through a folder and see which images need manual cropping.  My only other option would be to use imagemagick without the unsharp (which takes the longest) just to create a preview folder, but I would prefer to reduce the number of steps.

Has anyone run into a viewer that can do this?

Thanks,

Steve

---

### Post by mztriz on 2006-01-12
I don't know about an image viewer but you can change image size in the gimp.
[http://www.gimpguru.org/AskTheGuru/G20050312/](http://www.gimpguru.org/AskTheGuru/G20050312/)

---

### Post by Wes24 on 2006-01-12
Don't know whether it satisfies your needs, but you could try F-Spot:
[http://www.gnome.org/projects/f-spot/](http://www.gnome.org/projects/f-spot/)

I believe it is in the repositories, so you can install it using synaptic.

---

### Post by SteveF on 2006-01-12
[QUOTE=mztriz]I don't know about an image viewer but you can change image size in the gimp.
[http://www.gimpguru.org/AskTheGuru/G20050312/](http://www.gimpguru.org/AskTheGuru/G20050312/)[/QUOTE]

I thought about trying Gimp, but that requires opening files one at a time.  I might have over 100 images to be printed and I wanted to quickly scan them for those that don't look right because of cropping.

Thanks anyway.

---

### Post by SteveF on 2006-01-12
[QUOTE=Wes24]Don't know whether it satisfies your needs, but you could try F-Spot:
[http://www.gnome.org/projects/f-spot/](http://www.gnome.org/projects/f-spot/)

I believe it is in the repositories, so you can install it using synaptic.[/QUOTE]

Thanks.  I'll take a look at it.  I need a photo manager anyway so it might fit that bill even if it doesn't do the other.

---

### Post by stuporglue on 2006-01-12
Why not use Nautilus' image preview feature and throw all images you want (or don't want, depending) in a different folder? Then your imagemagic solution would still work. You can even change the size of the thumbnail in Nautilus to make viewing them easier.

EDIT:
Digicam, a KDE app, may have the feature you're looking for too. It's the best simple image library/touch-up program I've found yet.

---

### Post by SteveF on 2006-01-12
[QUOTE=stuporglue]Why not use Nautilus' image preview feature and throw all images you want (or don't want, depending) in a different folder? Then your imagemagic solution would still work. You can even change the size of the thumbnail in Nautilus to make viewing them easier.

EDIT:
Digicam, a KDE app, may have the feature you're looking for too. It's the best simple image library/touch-up program I've found yet.[/QUOTE]

The problem with using Nautilus is that the image does not appear in a 2:1 ratio.  It is the original image.  So I have to look at it and guess if it will get cropped badly.  What I would like in Nautilus or any viewr is an option to make all image icons fit a ratio and be cropped if it doesn't match.  I'm probably asking too much since I don't see a big ddemand for the feature.  I just tested imagemagick to a temp folder and it wasn't too bad when I removed the unsharp mask.  So I may just end up: 
running imagemagick without unsharp to a preview folder, 
scan for bad cropping, pull those out and crop them manually in the Gimp, 
then do the rest in imagemagick with the unsharp.

Since it runs in batch, I'll just kick it off and do other work.

I have Kubuntu loaded in another partition (I'm trying to stay either all gnome or all KDE if possible to) so I'll look at digikam (assuming that is the same app) next time I reboot and feel in a KDE mood.

Steve

---

### Post by elidoperezmd on 2007-10-08
picasa might be what you need

---

