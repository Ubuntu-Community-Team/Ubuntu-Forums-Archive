---
title: "How is this done?"
date: 2008-01-20
forum: Desktop Effects &amp; Customization
---

### Post by Majorflam on 2008-01-20
I just downloaded 7.10 and I got to say the improvements from 6.4 are awesome. I had given up on Ubuntu a year or so ago, but have tried again and I think I'm gonna love it.

Can someone tell me how this kind of setup is achieved?

[img]http://ubuntuforums.org/g/images/354557/large/1_ss3.jpg[/img]

---

### Post by nitromanrc on 2008-01-20
Compiz (fusion)...what graphics card do you have? i can help if you have nvidia...but other than that basically you gotta get the right drivers for your card so that you can enable compiz/desktop effects..after that you can install avant-window-navigator (google it) thats what i use for the dock, the one in the screenshot may be kiba-dock but i haven't used that personally...also look around on [www.gnome-look.org](www.gnome-look.org) for themes and icons...

There are lots of tutorials just google or search the forum for "enabling compiz with (INSERT BRAND OF GPU HERE) in ubuntu gutsy"...something along those lines should get you somewhere

as for avant window navigator...there is an install guide on their site: [http://wiki.awn-project.org/](http://wiki.awn-project.org/)

and for the themes/icons and stuff you just download the package off of [www.gnome-look.org](www.gnome-look.org) and then go to System-->Preferences-->Appearance and then simply drag the tar.gz package you downloaded from nautilus into the appearance window


I personally like the Black-White icon theme ([http://www.gnome-look.org/content/show.php/black-white?content=70299](http://www.gnome-look.org/content/show.php/black-white?content=70299)) and 
the osx -mod gtk2 theme 
([http://www.gnome-look.org/content/show.php/OSX-mod?content=58188](http://www.gnome-look.org/content/show.php/OSX-mod?content=58188))

good luck and welcome back to the community

---

### Post by Ub1476 on 2008-01-20
The dock there is [Kiba-Dock]("http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Dependencies"). [Avant-Window-Navigator]("http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository") is another alternative.  

Themes can be found on [gnome-look.org]("http://gnome-look.org/"). If you want something "mac-like", I suggest you search for Mac4lin.

Kiba-Dock and AWN requires composite, so you need to have Compiz-Fusion (visual effects) working. It can be located in System>Preferences>Appearance>Visual Effects.

If it's not working post the output of:

```
lspci | grep VGA

compiz
```

---

### Post by Majorflam on 2008-01-20
It's a NVIDIA card I'm using, I'm sure it's a geforce 256MB.

Do you have any how to's for this?

TIA

BTW I'm using 64 bit version of UBUNTU

---

### Post by Ub1476 on 2008-01-20
> **Majorflam said:**
> It's a NVIDIA card I'm using, I'm sure it's a geforce 256MB.

Do you have any how to's for this?

TIA

BTW I'm using 64 bit version of UBUNTU

Open the Terminal >Applications>Accessories>Terminal

```
lspci | grep VGA

```

---

### Post by rosegarden78 on 2008-01-20
> **Ub1476 said:**
> The dock there is [Kiba-Dock]("http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Dependencies"). [Avant-Window-Navigator]("http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository") is another alternative.  

Themes can be found on [gnome-look.org]("http://gnome-look.org/"). If you want something "mac-like", I suggest you search for Mac4lin.  Kiba-Dock and AWN requires composite, so you need to have Compiz-Fusion (visual effects) working. It can be located in System>Preferences>Appearance>Visual Effects.


cairo-dock is another entry in the Apple dock clones.  I've tried docks and they give me headaches.  The only dock or launcher I use comes with XFCE.  If you want speed, power and simplicity try an Ubuntu Gutsy system with KDE and XFCE installed.  Select XFCE as default session.  Then add "nautilus" to Settings - Autostarted Programs

I take speed, power and simplicity over eye candy *any* day.

---

### Post by Majorflam on 2008-01-20
> **Ub1476 said:**
> Open the Terminal >Applications>Accessories>Terminal

```
lspci | grep VGA

```

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

So that's my card. I'm assuming it's compatible, and if no-one posts back to say it isn't then I'll have a little toy around with the links on the previous posts.

Thanks guys.

---

### Post by Majorflam on 2008-01-20
> **Ub1476 said:**
> The dock there is [Kiba-Dock]("http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Dependencies"). [Avant-Window-Navigator]("http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository") is another alternative.  

Themes can be found on [gnome-look.org]("http://gnome-look.org/"). If you want something "mac-like", I suggest you search for Mac4lin.

Kiba-Dock and AWN requires composite, so you need to have Compiz-Fusion (visual effects) working. It can be located in System>Preferences>Appearance>Visual Effects.

If it's not working post the output of:

```
lspci | grep VGA

compiz
```

OH, I misread this post.

I don't seem to have a compiz-fusion option there. I have three options:

None
Normal
Extra

I've got it set to extra.

---

### Post by Majorflam on 2008-01-20
Guys, my systems messed up. I entered compiz into the terminal and got this output:
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

Now I've lost my desktop and the screen's going nuts.

---

### Post by Majorflam on 2008-01-20
Just to recap:

I have typed "compiz" into a terminal and the system seemed to go haywire. I've rebooted and it seems stable for now.

Do I need to reverse anything I've done here?

---

### Post by Ub1476 on 2008-01-20
You said you set it to extra with no errors like "desktop effects could not be enabled"? If so, Compiz works fine. If you want to have more settings for visual effects install **Advanced Desktop Effects** and set Visual Effects to custom. 

The links I provided has instructions on how to install a mac doc.

---

### Post by Majorflam on 2008-01-20
Thanks

---

### Post by rosegarden78 on 2008-01-23
Like this:
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
worked for me too on an Intel 915 graphics card.

---

