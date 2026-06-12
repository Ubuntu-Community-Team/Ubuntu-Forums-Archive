---
title: "easy win32codecs..."
date: 2005-12-22
forum: Desktop Environments
---

### Post by yeahyeahyeah on 2005-12-22
HI. I installed Ubuntu a few weeks ago, and I remember getting the Win32Codecs installed then without a problem. I don't remember having to un-tar or do anything.

Am I insane? Or is the only way to do it pretty complicated?

Thanks.

---

### Post by Sutekh on 2005-12-22
The easiest way I can think of is Automatix.
[http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by nalmeth on 2005-12-22
a really good way to go for this is a script like automatix or easy ubuntu.

[http://ubuntuforums.org/showthread.php?t=64629](http://ubuntuforums.org/showthread.php?t=64629) (easy ubuntu)
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563) (automatix)

there will be some minor tar/gzing if you want to use automatix, but very minor indeed. These will have what you're looking for and more i'm sure 
instructions on link

---

### Post by Sutekh on 2005-12-22
Automatix is now available as a .deb, and is very simple to install

```
wget http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb
sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb
```

Is all that's required.

---

### Post by dcstar on 2005-12-22
[QUOTE=yeahyeahyeah]HI. I installed Ubuntu a few weeks ago, and I remember getting the Win32Codecs installed then without a problem. I don't remember having to un-tar or do anything.

Am I insane? Or is the only way to do it pretty complicated?

Thanks.[/QUOTE]
Add this to your repositories and use Synaptic to install them:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

---

### Post by cjazz on 2005-12-22
Alternatively, you can add the ubuntu-plf repo with this line:

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

Peace.

---

### Post by dcstar on 2005-12-23
[QUOTE=cjazz]Alternatively, you can add the ubuntu-plf repo with this line:

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

Peace.[/QUOTE]
Quite right, I had the plf repository turned off on my system because the mirror I was using wasn't responding quite a few weeks ago (and the error messages were annoying me!)

---

