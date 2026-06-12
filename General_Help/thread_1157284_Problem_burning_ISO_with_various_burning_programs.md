---
title: "Problem burning ISO with various burning programs"
date: 2009-05-12
forum: General Help
---

### Post by Miata-MS on 2009-05-12
I am creating (or trying to) backup DVD's in my collection that my wife uses in her classroom and I do not want kids stealing my originals. So here I am trying to copy The Odyssey last night.

Quick tangent : Why is there no good method of ripping DVD's in linux (ie. DVDShrink?...had to use it through WINE)

OK, I have working ISO. Played it with VLC just fine. Archive Manager opens it up and can see the correct file structure inside the image.

I have tried to use GnomeBaker and Brasero, to simply burn the ISO to a DVD5 disc (file size is 4464MB). Both programs "successfully complete", eject the disc, and you can see where the disc has been written to (Thin little strip of 'unwritten' surface near the edge). Put the disc in the drive and *Nothing*. Tries to mount it, but does NOT show any files...however, it does NOT bring up the "Empty CD/DVD" dialog either. So I'm guessing it realizes the disk is not empty. VLC refuses to try to read the disc. And for whatever reason, both burning programs are 'completing', so there's no errors for me to look at and try to figure out what's going on.

Oh yeah, and it will "write" to the disc multiple times without producing an error as well. Even though you can physically see the section of the disc it previously wrote to. :confused:

Any ideas? BTW I'm on Jaunty. Thanks much.

EDIT : Solved this problem. Different disc and burned at 1x seemed to do the trick. Thanks for the input. I'll see if I can get k9copy to work next time.

---

### Post by coffeecat on 2009-05-12
> **Miata-MS said:**
> Quick tangent : Why is there no good method of ripping DVD's in linux (ie. DVDShrink?...had to use it through WINE)

Of course there is. Install k9copy from the repositories. You might need libdvdcss2 installed as well (from Medibuntu).

---

### Post by wsonar on 2009-05-12
k3b is a good burner also

---

### Post by Miata-MS on 2009-05-12
> **coffeecat said:**
> Of course there is. Install k9copy from the repositories. You might need libdvdcss2 installed as well (from Medibuntu).

I installed both of those.....k9copy would not copy the disk while DVDShrink grabbed it right away. Maybe i'm doing something wrong?

---

### Post by coffeecat on 2009-05-12
> **Miata-MS said:**
> I installed both of those.....k9copy would not copy the disk while DVDShrink grabbed it right away. Maybe i'm doing something wrong?

k9copy works for me just fine - has done with each version I've tried since Hardy. If the DVD is encrypted you have to install libdvdcss2, otherwise k9copy hangs or crashes (which is hardly surprising). Exactly how would k9copy not copy the disk? Did you get any errors?

---

### Post by Miata-MS on 2009-05-12
> **coffeecat said:**
> k9copy works for me just fine - has done with each version I've tried since Hardy. If the DVD is encrypted you have to install libdvdcss2, otherwise k9copy hangs or crashes (which is hardly surprising). Exactly how would k9copy not copy the disk? Did you get any errors?

The disc is encrypted, I know that much. I used aptitude to install both k9copy and libdvdcss2 and it would just hang trying to open the disc. Only error was something like "Cannot open disc". Even RipIt4Me wouldn't open the disc... I think I'm just working with a crazy ISO... I downloaded a copy of the RC for Windows 7 and burned that on the same brand of media on the same burner with no issues at all.

I'm in the middle of trying a new disc right now burning at 1x just to make sure my burner isn't at fault, but it's been working great up til now, so I'm not sure where to start looking for problems. Given the difficulty I had ripping the DVD to begin with, maybe it's just the movie... ?

---

