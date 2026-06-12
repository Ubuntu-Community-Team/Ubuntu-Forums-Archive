---
title: "Serpentine problem"
date: 2005-11-17
forum: Desktop Environments
---

### Post by tedius on 2005-11-17
I'm having a problem burning audio CDs with Serpentine (I haven't tried anything else yet)

I'm trying to burn a load of *.ogg files to an Audio CD and all goes well until I try to write to disc.  It gets up to 50% where it says that it is preparing the cd-writer.  I can hear the disc spining up and then down again, and so it continues, and never gets anywhere.

I have no problems writing data CD or Audio if I do a disc copy, only Serpentine is the problem :confused: 

Does anyone have any idea what this may be, or at least where I can start looking.

Thanks

---

### Post by Ampersand on 2005-11-17
Try running serpentine from a terminal, nd see whether it gives you any errors or messages when it stops working.

---

### Post by StefanoCole on 2005-11-17
I also was unsuccessful in burning a CD with wav files using Serpentine. When I started the process Serpentine said it was going to prepare files for burning but, after that, nothing else happened. Then, from a terminal I tried cdrecord and I was successful in burning the CD. The command that I used was:
$ cdrecord dev=/dev/hdc *.wav
(my cd burner is /dev/hdc)

I don't know if you could type something like: cdrecord dev=/dev/hdc *.ogg

In my case command line applications seem to work better than graphical ones. ;) 

Bye, Stefano

---

