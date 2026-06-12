---
title: "Burning / Watching .img DVD ISO image"
date: 2006-06-04
forum: Desktop Environments
---

### Post by gnu2tux on 2006-06-04
Hi, 

  I recently obtained a movie (legally, I might add) which is provided in .img format.

I noted that K3B didn't recognise the img file to burn, so I renamed it to .iso and K3B noticed it was an ISO image. The checksum checked out fine, so I burnt it to a DVD-R. No problems.

Once I opened the DVD up in kmplayer (my usual dvd playing software), it did not recognise a dvd movie in a disc. I opened the disc up in konqueror and I noticed the VIDEO_TS directory and all the chapters for the disc in it. I could even open the chapters and I think (if memory serves) they played back OK.

So I guess there is something I need to do in order to tell k3b that it's a DVD movie, not a DVD data disc - am I right? Or am I missing the point and .img files are something else entirely?

This is annoying me now as I note that most DVDs that I can now get my hands on are all in .img format.

Can anyone help?

Many thanks!

Al

---

### Post by disturbed1 on 2006-06-04
.img files that were created in Windows are made (*usually*) with one of 2 programs, Spruce Technologies SpruceUp and/or DVD Maestro, or img tools. They are exactly the same file as an iso image.

Rename the file to .iso , drag n' drop onto VLC. VLC will play .iso DVD images with menus. If it doesn't play it most likely wasn't authored correctly.

You can also mount the iso. Create a folder in /home/$user/iso
sudo mount -o loop -t iso9660 filename.iso /home/$user/iso

---

### Post by gnu2tux on 2006-06-04
Thanks thats great, but I would rather store these in DVD format as they are intended onto a DVD disc, as my hard  drive is filling up fast!

Any suggestions on actually making it a DVD image rather than just a standard iso image?

Cheers,

Al.

---

### Post by taurus on 2006-06-04
Actually, you can burn .img as an .iso image with k3b.  No need to convert anything.  Just tell k3b where the file is and tell it to show everything.  I have burnt a few .img files with k3b directly and they are working just fine.

---

### Post by disturbed1 on 2006-06-04
[quote=gnu2tux]Thanks thats great, but I would rather store these in DVD format as they are intended onto a DVD disc, as my hard  drive is filling up fast!

Any suggestions on actually making it a DVD image rather than just a standard iso image?

Cheers,

Al.[/quote]

Just burn it ;)

I gave you suggestions on how to check the file out before burning:-D

---

### Post by gnu2tux on 2006-06-05
I did that - I mounted as loopback and it seemed fine when mounting as type -t udf (rather than iso9660).

But if I burn the disc it appears as a data disc - :(

Al.

---

### Post by disturbed1 on 2006-06-05
Then it most likely wasn't authored correctly. All of my dvds mount as iso9660 (which udf is a subset of). If the person that created the img file chose the wrong UDF version (2.0 instead of 1.2) you could have this issue.

With the image mounted, open K3B and select to author a video dvd, drag and drop the complete contents of the VIDEO_TS directory (all of the .IFO .BUP & .VOB files), then try to burn it again.

---

### Post by gnu2tux on 2006-06-12
Many thanks - i'll give that a try tonight.

Al.

---

