---
title: "nautilus displaying mp3 thumbnails"
date: 2005-08-22
forum: Desktop Environments
---

### Post by vaskark on 2005-08-22
I have cd cover images inside most of my mp3's. Is nautilus capable of displaying them? If so, is there an extra package I need to install for this to work? I already know that you can use an image file as a custom icon for the mp3 file - I'm just hoping I won't have to go through all that for every music file i have.

Thanks.

---

### Post by maubp on 2005-09-28
Thats more or less the exact question I was going to ask...

I assume this would be a new "extension" to the code, in the same way that nautilus must open image files to generate their thumbnails, it could open music files (mp3 or ogg) to check for any image in the ID3 v2 tags, and use that as the thumbnail.

Would this be an enhancement to nautilus itself, or some sub library?  Where would I go to log a bug/enhancement request?

---

### Post by maubp on 2005-10-25
Anyone?

---

### Post by Alexander Kirillov on 2005-10-25
[QUOTE=maubp]Thats more or less the exact question I was going to ask...

I assume this would be a new "extension" to the code, in the same way that nautilus must open image files to generate their thumbnails, it could open music files (mp3 or ogg) to check for any image in the ID3 v2 tags, and use that as the thumbnail.

Would this be an enhancement to nautilus itself, or some sub library?  Where would I go to log a bug/enhancement request?[/QUOTE]
I do not think Nautilus does it. 

One possibility for it to happen is if a music player (e.g. rhythmbox or banshee) creates thumbnails for each MP3 file - much like, say, evince creates thumbnails for PDF files. Or Nautilus could create the tnumbnails itself. 

You can file a feature request for this in GNOME bugzilla bugzilla.gnome.org - use product Nautilus or rhythmbox. However, beware: there are way too many bugs for Nauitlus, and developers are buried under all the bug reports they are getting. So chances of them actually acting on this one are small. 

You could also try discussing it in one of mailing lists (e.g., rhythmbox one) at [http://mail.gnome.org/mailman/listinfo/](http://mail.gnome.org/mailman/listinfo/)

---

