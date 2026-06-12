---
title: "mjpegtools and cinelerra - about to give up"
date: 2005-01-16
forum: General Help
---

### Post by fsman on 2005-01-16
I decided to switch from mandrake to ubuntu.
I really need mjpegtools and cinelerra - these were easy to install for mandrake using its sw control centre.

Now in ubuntu I can't find it in synaptic and a google of debian isn't helping either.

I did follow another post to download the cinelerra binary rpm, alien and dpkg -i.

but i get the following error

cinelerra: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory


Question is : is there a ubuntu repository for mjpegtools and cinelerra?
or how to get rid of the above error message?

---

### Post by gratefulfrog on 2005-04-22
[QUOTE=fsman]
Question is : is there a ubuntu repository for mjpegtools and cinelerra?
or how to get rid of the above error message?[/QUOTE]

I've compiled both of these from source, and also managed to install them from debian packages. However, I can't make cinelerra work on my 64bit Hoary to save my life.
Try downloading cinelerra from heroinewarrior, that should install ok on Hoary.

Please let me know if you ever manage to make it work!   :-)

---

### Post by gratefulfrog on 2005-05-08
Since the last entry, I have been able to get the whole thing to work:

- capture with 64bit home-built dvgrab, or Kino under a 32bit chroot Ubuntu,
- edit & render with cinelerarra built from source taken from heroinewarrior,
- convert to mpeg2 with ffmpeg (built from cvs snaptshot Ubuntu's repository contains and old and defective version)
- build iso image with dvdstyler
- burn the dvd with nautilus!

All this on an AMD64 with 64bit Ubuntu!

It was tough but it can be done!  \\:D/

---

### Post by fsman on 2005-05-08
I upgraded to hoary for xorg.
then downloaded the RPM from the cinelerra site
and used alien and dpkg as per the ubuntu guide.
all happy now, but a shame that it isn't in the repos.

---

