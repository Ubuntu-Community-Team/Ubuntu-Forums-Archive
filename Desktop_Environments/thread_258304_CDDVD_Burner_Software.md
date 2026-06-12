---
title: "CD/DVD Burner Software"
date: 2006-09-15
forum: Desktop Environments
---

### Post by SonWon on 2006-09-15
Is there a CD/DVD burner program that will allow you to create data CDs that you can still add more files to the CD after the first burn?  In other words you do not close the CD.  I have already looked at GnomeBaker and did not see this feature.

Thank you,

---

### Post by maniacmusician on 2006-09-15
K3b

---

### Post by SonWon on 2006-09-15
I thought k3b was a KDE application, can I run it in gnome?

Thanks,

---

### Post by bribri124 on 2006-09-15
Yes you can use K3B.  Great app with cool sounds.

---

### Post by SonWon on 2006-09-16
Thank you, I'll check k3b out.

---

### Post by SonWon on 2006-09-17
K3B is sweet.  It has many more options than GnomeBaker.

I don't see which setting controls keeping the CD open or closed when burning the CD.  I probably just don't understand all of the options.  Can someone point me to the setting that controls this feature when burning a data CD?

I tried to use the manual but it didn't work since I am using Gnome.

Thank you,

---

### Post by lamego on 2006-09-17
If you plan to test Gnome Baker please give a try to the latest version (0.6.0):

[I]NOTE: This is an unoffical package created by myself, by installing it you are trusting me.
[/I]
[http://www.getdeb.net/getdeb.php?file=gnomebaker_0.6.0-0ubuntu1_i386.deb](http://www.getdeb.net/getdeb.php?file=gnomebaker_0.6.0-0ubuntu1_i386.deb)

---

### Post by SonWon on 2006-09-18
I tried out 0.60 from the sourceforge website.  I don't see how to burn a CD and leave it open so additional files can be added later?

I used make install to load gnomebaker but now I can't find a way to uninstall?  Do I need to do this manually?  And how please?

Thank you,

---

### Post by jimbob on 2006-09-18
I think if you use the CD+RW format k3b will allow you to remove the CD and     then put it back in at a later time and add to it.

I successfully performed this several months ago but I forgot exactly what I had to do.

---

### Post by SonWon on 2006-09-18
I can test that.

Nero on Win XP has a check box that forces the CD-R open or closed.

Thanks,

---

### Post by lamego on 2006-09-18
SonWon,
if you have used "make install" without checkinstall then the only way is to manually delete the files.

You should have installed from a .deb package to make your life easier ;)

---

### Post by SonWon on 2006-09-18
How does the checkinstall work?  I remember using checkinstall.  I thought it just checked  for missing packages?

Hmm, I could have trusted you I suppose, but then how would I learn?

Thank you,

---

### Post by tube on 2006-09-20
> **lamego said:**
> SonWon,
if you have used "make install" without checkinstall then the only way is to manually delete the files.

You should have installed from a .deb package to make your life easier ;)Or you can use "(sudo) make uninstall" in the source folder, which is a bit easier than the manual way ;). If you already got rid of the source, just extract the source package and configure (no need to make && make install) it the same way you did before so it'll know what to uninstall.

---

### Post by SonWon on 2006-09-21
Okay, it worked!

Here is what I did.

Downloaded the source, ran ./configure, ran make uninstall, and now it is gone.

Thank you,

---

### Post by SonWon on 2006-09-29
Tried my first DVD with k3b and it failed, even locked the drive?

I reloaded gnombaker 0.5.1 and it worked!  I didn't noticed this before but with DVDs there is a finalize option.  The option does not appear with CDs?  Anyway it looks like I'll be using gnomebaker for now.

---

