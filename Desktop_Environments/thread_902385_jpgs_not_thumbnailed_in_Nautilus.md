---
title: "jpgs not thumbnailed in Nautilus"
date: 2008-08-27
forum: Desktop Environments
---

### Post by DavidTangye on 2008-08-27
After an untidy upgrade to Hardy that needed me to run 'dpkg --configure -a' to fix the upgrade (see [this bug report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/249340") for the background), everything seems to be working ok. However in Nautilus, jpg files are indicated by an icon for text files, and no thumbnail is created for display in Icon View. pngs gifs .xcfs are all fine.

How do I fix this?

---

### Post by bmac on 2008-08-29
One thought.

Check your configuration editor.

gconf-editor/apps/nautilus/preferences/show_image_thumbnails

Make sure this isn't set to never. If so change it....


Hope this helps......

---

### Post by DavidTangye on 2008-08-30
Thanks, but its not set to never, besides it only affects jpgs.

---

### Post by bmac on 2008-08-30
In your nautilus file browser the edit/preferences/preview tab
"Show thumbnails" is specifically for showing thumb nails of image files "Always" "Local Files Only" "Never". 
The following section defines the size of the image file permitted - Only for files smaller than "10 meg or ????". Is it possible that your image files are larger than the size selected in that box?

My only other thought is that this issue is somehow related to a theme. Hopefully, we can get someone else involved in this request as I'm out of ideas.....

---

### Post by felixtz on 2008-09-09
To give feedback to this thread (I am not the OP, but found this thread thru Google).

Thanks!

The file size limit was my problem. Some jpg files showed ok, some did not. 12-megapixel camera. JPEGs were right on the 5 meg (setting limit) wire.

---

