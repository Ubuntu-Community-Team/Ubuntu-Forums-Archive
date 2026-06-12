---
title: "[SOLVED] Webcam works with everything except cheese"
date: 2008-12-10
forum: General Help
---

### Post by blakjesus on 2008-12-10
Cheese used to be able to detect my webcam just fine, but after going back to it after a week or so after installing it, Cheese just shows a blank screen.

I can get my webcam to work just fine in VLC.

If it helps any, i tried running cheese through a terminal and this was the output:

> (cheese:32752): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:32752): WARNING **: could not generate thumbnail for /home/phil/Videos/Webcam/2008-12-10-183607.ogv (video/ogg)


(cheese:32752): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:32752): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small


Any suggestions? :confused:

---

### Post by nhasian on 2008-12-10
yes this should get cheese working again:

[http://bugzilla.gnome.org/show_bug.cgi?id=545033](http://bugzilla.gnome.org/show_bug.cgi?id=545033)

---

### Post by blakjesus on 2008-12-10
No good.

I ran:
make
sudo make install PREFIX=/usr/local

It seemed to be doing something and no errors showed up but im still not getting anything in Cheese.

---

### Post by tornadof3 on 2008-12-10
I have this exact some problem and would be interested in any fixes. Webcam is just grey in cheese, but works fine in VLC...

---

### Post by blakjesus on 2008-12-11
This actually did work for me. I didn't work earlier because i didn't know i had to reboot, but its working great now. Thanks :D

---

### Post by tornadof3 on 2008-12-11
OK so I downloaded the file libv4l-0.3.7.tar.gz from the link in that bugzilla post. I ran make and then sudo make install PREFIX=/usr/local. All looked well and no errors. I then rebooted. I still have the same problem, in Cheese, I just get a grey screen (the blue light next to the web cam shows it is on and working). In VLC it works fine.

I tried disabling desktop effects (compiz) etc to no avail. This is a HP 6735s laptop with the ATI drivers installed. Any ideas??

PMR

---

### Post by blakjesus on 2008-12-11
Trysing the 0.3.8 version from the link. (Its further down the page in the comments) Thats the one i used and it worked. Someone said that the 0.3.7 was missing something.

---

