---
title: "S-Video Help"
date: 2007-11-03
forum: Desktop Environments
---

### Post by Persianelfster on 2007-11-03
I've been trying on my own for a while now to get tv-out/svideo out to work for a while.  When i connect my machine to tv with svideo out the ubuntu loading screen appears with the bar, however once it is fully loaded, and the login window starts up, it goes blank.  From what i can find i believe this is a xorg config issue, can anyone tell me how i can add tv out to my xorg?

---

### Post by benerivo on 2007-11-04
If you have an NVidia card, you could try installing the nvidia configuration packages from the repositories. Search for nvidia and it will bring up a few to choose from. I had mine working using one of these packages (i can't remember which one) on my old computer.

---

### Post by forestpixie on 2007-11-04
I have to enable tv out for my nvidia with nvidia-settings which gets installed with the driver

make sure you've got a backup just in case it doesn't do it for you

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then run nvidia as root

```
gksudo nvidia-settings
```

you can enable the tv out there - 

that of course assumes you've an nvidia card and that you have the drivers for it installed.

---

### Post by Persianelfster on 2007-11-04
thats the problem.. i don't have a nvidia card, well not on the machine i want to enable it for =(

---

### Post by forestpixie on 2007-11-04
so what do you have then?
 if you don't know enter > lspci in a terminal and it'll tell you, if you're not sure post it here

---

### Post by Persianelfster on 2007-11-04
its a Trident Cyberblade /i1 rev 6a
if it helps it is one of those via mini itx boards

---

### Post by forestpixie on 2007-11-04
what does this give you

```
glxinfo | grep render
```

I assume if you go to restricted drivers it says there's nothing needed

Edit - if you search in multimedia forum for trident cyberblade there are a few threads - don't know if you've looked there

---

### Post by Persianelfster on 2007-11-04
at@at-desktop2:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
No Restricted Drivers

---

### Post by forestpixie on 2007-11-04
Wish I could more but I suggest you try having a look through the forum I pointed you at earlier.

It might be that you'll not be able to do it - I don't really know enough to say more than I have I'm afraid

---

### Post by Persianelfster on 2007-11-04
ill try i just need to figure out how to add it into my xorg file.

---

