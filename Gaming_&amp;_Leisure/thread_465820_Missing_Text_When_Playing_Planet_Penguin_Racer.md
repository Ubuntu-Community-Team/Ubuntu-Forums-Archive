---
title: "Missing Text When Playing Planet Penguin Racer"
date: 2007-06-06
forum: Gaming &amp; Leisure
---

### Post by muffinman on 2007-06-06
Since doing a fresh install upgrading from Ubuntu 6.10 to 7.04, when playing Planet Penguin Racer most of the text is shown as underscores (See attachments). If you remember which option to click on you can still play the game but it would be better if the text appeared.
Anyone else had this issue? 
Thanks in advance.

:)

---

### Post by madmetal on 2007-06-07
do you still have 3D acceleration enabled?
the easiest way to solve this is to re-install the game..
;)

---

### Post by Andrej_BB on 2007-06-15
I have the same problem. Fresh install on feisty 7.04. What should i do ?

---

### Post by DoktorSeven on 2007-06-15
If you run **ppracer** from a terminal, do you get any output regarding fonts or any other problems?

---

### Post by charlysbrother on 2007-06-27
I have the same problem. there is no output regarding fonts. game works fine apart from that. I'm running 64bit version.

---

### Post by samichx on 2007-07-27
Is there anything to get this working properly? I used to have ATI issues that I would sum this up to, now eery other program on the books and most wine programs work. Still no text in PPR.

---

### Post by User-007 on 2007-08-14
Hi!

For some people the following procedure has been a way to get out from that problem.

Try the following:

download older libgl1-mesa-dri from [http://packages.ubuntu.com/edgy/libs/libgl1-mesa-dri](http://packages.ubuntu.com/edgy/libs/libgl1-mesa-dri) (choose the right file!)

download older lilgl1-mesa-glx from [http://packages.ubuntu.com/edgy/libs/libgl1-mesa-glx](http://packages.ubuntu.com/edgy/libs/libgl1-mesa-glx)

And in the terminal

```

sudo dpkg -i /path/to/libgl-mesa-glx_6.5.1....deb
sudo dpkg -i /path/to/libgl-mesa-dri_6.5.1....deb

```

Replace "/path/to" with your download folder. This procedure downgrades ligl1-mesa to the edgy version and it should be a way to get the text into the menus of certain opengl applications.

I have not noticed any problems in my system when using older versions of software mentioned above. If you meet problems, you can always update the packages with synaptic or apt-get.

I would be very pleased to get any comments also.

Edit: I wonder is there any way to prevent the upgrading of downgraded packages? Now my system is always notifying that there are newer versions available for these packages. But, I don't want, because I love PPRacer.

Cheers,
User JB

---

### Post by samichx on 2007-08-16
Beautiful, not only does the downscale work for fixing planet penguin racer it also works when you take Gutsy packages. Turns out things do work out in the end.

---

### Post by User-007 on 2007-08-17
> **samichx said:**
> it also works when you take Gutsy packages..

Yes, that's true. Only bad point is that this is quite tricky way to get a cleanly installed system since there appears broken packages, But after a little work it is possible to get rid of them. For me, at least.

Thanks
User JB

---

