---
title: "[SOLVED] wmv videos fail to show thumbnails"
date: 2008-12-03
forum: General Help
---

### Post by jimbob on 2008-12-03
I have two *.wmv files which play fine but fail to show thumbnails and when I try to display their properties they fail to open the properties window which hangs there forever.

These same two files act normally on my Intrepid Beta distro that I have on another partition.

I have deleted and recopied them from there but the problem persists.

---

### Post by jimbob on 2008-12-04
Maybe someone could move this to the multimedia and video forum?

---

### Post by jimbob on 2008-12-10
bump

---

### Post by jimbob on 2008-12-14
last bump before I give up ...

---

### Post by jimbob on 2008-12-16
I fixed my problem but I don't really know how.  Maybe some Ubuntu multimedia guru can explain it.

I noticed that these 'bad' wmv's would play fine using totem-xine instead of the default (I think) totem-gstreamer, however they still wouldn't show thumbnails.  I was trying to figure out how to change the default movie player to totem-xine but I didn't (still don't) know how.

I decided to try getting rid of totem-gstreamer and re-installing it.  After entering apt-get remove -purge totem-gstreamer and doing an rm -rf .thumbnails, suddenly all of my 'bad' wmv's began showing thumbnails and everything worked great.

Is it that totem-gstreamer and totem-xine can't co-exist?  I really don't know.

---

