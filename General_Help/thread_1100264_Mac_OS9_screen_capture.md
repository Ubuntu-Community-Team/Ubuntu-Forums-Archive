---
title: "Mac OS9 screen capture"
date: 2009-03-19
forum: General Help
---

### Post by Random Adam on 2009-03-19
Hi I have a problem, I can't open the screen capture files from mac os9 on my home computer. 

They are the only computers on campus that run a specific application, which has gone out of production, thus the university must keep a few old mac's around to run it. Any idea how to convert these files to a useful format would be greatly appreciated.

---

### Post by BUSHYBOB on 2009-03-19
Openoffice draw can open them.

---

### Post by 3rdalbum on 2009-03-24
On Windows, Unix and Linux, any file you create will only have one part to them; the "data fork". The classic Mac OS was different in that some files had the data fork and a "resource fork". If you transferred one such file to a different operating system, the resource fork would be discarded.

PICT files, which the classic Mac OS saves screenshots into, contain all their image information in the resource fork - so as soon as you transfer the PICT file to your Linux box, you lose the image data.

Your best bet is to use the Mac OS 9 computers to convert the image to a cross-platform format such as JPEG, PNG, or TIFF. The Quicktime Image Viewer program should be installed on the Mac and it is capable of converting the image, just as long as you set the magnification of the image to "100%".

I'm not entirely sure if Image Viewer can do image conversions without paying for Quicktime Pro, but I hope it can. If not, then there are image editors on classic Mac OS that can do the job. A JPEG, PNG or TIFF created on the Mac will store all its data in the data fork and can be transferred to a Linux computer without problems.

@BUSHYBOB: Openoffice.org can only open PICT on the Macintosh for the above reason.

---

### Post by BUSHYBOB on 2009-03-26
I have a G3 mac and I copied a screenshot to one of my linux boxes and opened it in openoffice draw. No problems after giving it a .pict extension.

[IMG]http://www.paranormal.org.uk/mustardland/gallery2.php?g2_itemId=1319[/IMG]

---

### Post by BUSHYBOB on 2009-03-26
screenshot here

[http://www.paranormal.org.uk/mustardland/gallery2.php?g2_itemId=1319](http://www.paranormal.org.uk/mustardland/gallery2.php?g2_itemId=1319)


[IMG]http://www.paranormal.org.uk/mustardland/gallery2.php?g2_itemId=1319[/IMG]

---

