---
title: "Nautilus Sound Preview."
date: 2005-10-13
forum: Desktop Environments
---

### Post by chadwick359 on 2005-10-13
In nautilus, when you hold the mouse over a .wav file, it begins playing the file right in window. Is there a way to get it to do this with .ogg and .mp3 as well? They both pop up with at note emblem, so Nautilus knows that they are music files, it just doesnt preview them. Any input would be appreciated.

---

### Post by kassetra on 2005-10-13
[QUOTE=chadwick359]In nautilus, when you hold the mouse over a .wav file, it begins playing the file right in window. Is there a way to get it to do this with .ogg and .mp3 as well? They both pop up with at note emblem, so Nautilus knows that they are music files, it just doesnt preview them. Any input would be appreciated.[/QUOTE]

if I am not mistaken - you need to have mpg123 installed for .mp3 preview... ogg may require the same or it's own little player.

Of course, you need the lame / mad codecs installed to hear mp3s - do you have those installed?

---

### Post by chadwick359 on 2005-10-13
I do have lame and mad, but don't have mpg123... and synaptic seems to be busted atm... Thanks for the input, i'll post restult when I manage to get the package installed.

---

### Post by chadwick359 on 2005-10-14
Ok, I installed mpg123, and I still don't have any .mp3 preview in Nautilus, should i try a different mpg123 package? I don't see one for alsa, or i would have just installed that by default.

---

### Post by exosyst on 2005-10-15
You may need to remove your old thumbnails for this to work, e.g.:

```


exosyst@endosystem:~$ rm -rf ~/.thumbnails/normal/*
exosyst@endosystem:~$ rm -rf ~/.thumbnails/fail/*
exosyst@endosystem:~$

```

Should help.

---

### Post by bb002 on 2005-11-26
Thanks exosyst. I've been unable to get the sound preview to work for anything until I saw your little piece of code. Thanks again!

---

### Post by stalefries on 2005-11-26
I think you need the proper codecs. Try doing a google search for "nautilus sound preview mp3 ogg"

---

### Post by Aeon17x on 2005-11-29
[QUOTE=kassetra]if I am not mistaken - you need to have mpg123 installed for .mp3 preview... ogg may require the same or it's own little player.

Of course, you need the lame / mad codecs installed to hear mp3s - do you have those installed?[/QUOTE]

This one worked for me. I also cleared the thumbnails, but I noticed no difference other than my thumbnails folder having some breathing space.

---

### Post by Gray. on 2005-12-03
I am having a problem with previewing .ogg files in nautilus. I can preview .mp3 files easily. I tried the solution given by exosyst but it didn't work. I checked Synaptic and have vorbis-tools installed which contain ogg123. Any help would be greatly appreciated.

---

### Post by Gray. on 2005-12-04
No-one has any idea?

---

### Post by Gray. on 2005-12-09
*GRAGGGHGHGHGHLLLE* This thread has been brought from the dead to see if anyone has solved this issue and could help me out.

---

### Post by thoreauputic on 2005-12-15
Known bug I'm afraid - appears to have been around for a while - not an Ubuntu bug but an upstream one: 

See

[http://bugzilla.ubuntu.com/show_bug.cgi?id=6735](http://bugzilla.ubuntu.com/show_bug.cgi?id=6735)

Odd that mp3 works , but ogg doesn't ;) Seems backwards....

---

### Post by H.E. Pennypacker on 2006-07-22
Radical!  I have never known about this preview feature.  Windows certainly does not have such a feature.  Awesome.  It works with MP3s too.

---

### Post by chadwick359 on 2006-07-23
What the carp necromancy, sir?

---

### Post by natern on 2007-04-11
Thanks! I thought I had mpg123 already installed, but it must have been another system because that definitely fixed the problem!

---

