---
title: "HUUUUGGGEEE bug with the file viewer/Nautilus 2.24.1"
date: 2009-03-30
forum: Desktop Environments
---

### Post by touristguy87 on 2009-03-30
Hi, I have to report a HUUUUUUGE monster bug in 
Nautilus 2.24.1

with regards to saving an image. 

the problem is that it will happily overwrite an image even if the "user" tells it to save the image with a different name, IF the target file was original selected from the "recent files" list.

Try this. 

1-View a page on the web that has a jpeg, thusly:

[http://www.flickr.com/photos/focusman55/3398649768/](http://www.flickr.com/photos/focusman55/3398649768/)

2-right-click on the image, save it to your desktop. 

3-find the image on the desktop, double-click it, it will open in a viewer. Close the image. The image should now be at the top of the "recent documents" list. Check this by going to the places menu and then "recent-documents", the top entry should open to the same image. 

4-save the image (or any other image) again, the same way, but this time in the "save image" dialog click on "recently used" in the left part and click on the top entry in the list, on the right side. You should see the picture on the right (in a thumbnail viewer) and the filename at the very top in the file-box. Click on the name and *change the name* in the filename dialogbox, then hit alt-s to save the file under that name. 

Right? 

Wrong. 

You just overwrote the original image. 

Try it again, this time using the "desktop' link on the left side, then clicking on the image-file, then changing the name in the "filename" dialog. Hit alt-s or save. Now you have a new file with that name containing the image that you want to save. 

As long as you select an entry in the "recently used" file list just before saving, you will overwrite that file, regardless of whatever you have set the "filename" dialog to. Not only will it save the file with that name regardless of whatever you put in, it will save it in that *directory* (which was the point of my using the "recently used" list in the first place).

How's that for a quick & easy way to lose a few days worth of work?

---

### Post by Mr. Picklesworth on 2009-03-30
Eeek!
Just so you know, that's actually a bug with GTK from the sounds of it. (Any file chooser dialog is probably made by GTK).

Also, this isn't really a support request. This kind of information is REALLY valuable, but not all that helpful when it's in the wrong place. Ubuntu's development and bug tracking all happens over at Launchpad.net. Feel free to file your bug there!
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

This is probably actually an issue upstream (one of the components Ubuntu ships but doesn't build), so if you feel like it you can actually poke through [http://bugzilla.gnome.org](http://bugzilla.gnome.org) and file it there, but you can really just put anything like this on Launchpad and it will be taken care of. (Naturally, it's courteous to do what you can towards avoiding duplicates and filing it against the correct projects).

And yes, this will help you, too! All the work towards fixing the issue is centered around your bug report, so as well as having that nice "I contributed!" feeling, you get to know what the status is towards getting it resolved.

---

### Post by touristguy87 on 2009-03-30
done
thanks

---

### Post by 3rdalbum on 2009-03-31
Congratulations for finding and reporting the bug, thanks for helping to improve the software I use :-)

---

### Post by touristguy87 on 2009-04-10
one other question..is there any info on the KDE/gnome battle, or running them both at the same time? 

I might have to look into this...

thanks

---

