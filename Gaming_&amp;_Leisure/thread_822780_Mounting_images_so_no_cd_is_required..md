---
title: "Mounting images so no cd is required."
date: 2008-06-08
forum: Gaming &amp; Leisure
---

### Post by therock003 on 2008-06-08
I want to play this game i have and there does not seem to be a no-cd patch available,so i was wondering how can i mount an image file of the cd,so its not required to be on the drive,when i decide to launch it.

---

### Post by V for Vincent on 2008-06-08
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

Haven't tried it out, but it's supposed to work.

---

### Post by therock003 on 2008-06-08
Thanx but i have already found that out.Thing is i'm a new linux user and i dont know how to get instal and configure it.I've reached as far as the souceforge page where it has like 5-6 which one do i get,how do i install it and how do i then mount the image?

Sorry that i'm asking that much,but i'm really new to linux and i'm having difficulties.

---

### Post by Grishka on 2008-06-08
get AcetoneISO: [http://getdeb.net/app/AcetoneISO](http://getdeb.net/app/AcetoneISO). it's like Windows' Daemon Tools.

---

### Post by doorknob60 on 2008-06-08
Or this guide should work: [http://ubuntuforums.org/showthread.php?t=719270](http://ubuntuforums.org/showthread.php?t=719270)

---

### Post by therock003 on 2008-06-08
Oik i tried it,nice options but doesnt work with my image.I tried mounting it as a bin,and didnt work.Then i tried converting it to iso from inside the program and still nothing.

---

### Post by Grishka on 2008-06-08
what's the image format?

---

### Post by therock003 on 2008-06-08
initial format is ccd and bin,and i've converted it to iso.

I also tried that sh method but i cant change it to allow execution on properties.For some reason the check poppes back out.

I also get an error mounting with the gmount option.

---

### Post by Grishka on 2008-06-08
> **therock003 said:**
> initial format is ccd and bin,and i've converted it to iso.

I also tried that sh method but i cant change it to allow execution on properties.For some reason the check poppes back out.

I also get an error mounting with the gmount option.

that's odd. isos should mount without problems. try gmount-iso for that. also, it might help if you tell us the exact error message you're getting.

---

### Post by therock003 on 2008-06-08
At the gmount i actually get an error that could not mount as user root
how do i circumvent that?

---

### Post by therock003 on 2008-06-08
> **Grishka said:**
> that's odd. isos should mount without problems. try gmount-iso for that. also, it might help if you tell us the exact error message you're getting.

Failed to run mount ... .......blah blah **as user root**

---

### Post by Grishka on 2008-06-08
> **therock003 said:**
> Failed to run mount ... .......blah blah **as user root**

man, don't skip the blah blah part. :-) give the exact error message. otherwise it's hard to tell what could be wrong. also, pray tell what AcetoneISO complains about.

---

### Post by therock003 on 2008-06-08
the exact message is stating the location of the image and the folder i've selected to be mounted on and it is irelevent.The gold is that it cant mount the image as user root.

How do i get passed that?

That's what gmount says.

Acetone just gives a plain "Error could not mount image" <- exact message an then "Solution:http:/acetone..." oints to the homepage i guess.

---

### Post by Grishka on 2008-06-08
> **therock003 said:**
> the exact message is stating the location of the image and the folder i've selected to be mounted on and it is irelevent.The gold is that it cant mount the image as user root.

How do i get passed that?

That's what gmount says.

Acetone just gives a plain "Error could not mount image" <- exact message an then "Solution:http:/acetone..." oints to the homepage i guess.

oh yeah, the blah blah part is your file path, just realised what you meant by that, silly me. ;) unfortunately, I'm not sure what could be the problem, the error message is not very verbose. but try following the link given by AcetoneISO and see what it reads.

---

### Post by bulletxt on 2008-06-08
first of all, tell us what type of image it is. is it a multisector image? is it a cdaudio image? please tell us more about it.

if you can't convert the image with acetoneiso, I'm suspecting it is a vcd or cdaudio image or a game created in multisector mode. you simply can't convert it to is because ISO filesystem does not support multi track images. if this is the case, the only solution at the moment is to try and use cdemu because it is the only one capable of managing multisector images. the only problem is making it work!

anyways, the link acetoneiso gives to you, wich is actually the manual, talks about these type of errors and warns about multisector images.

---

