---
title: "X1950 Pro + Driver Problem"
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by yellowindian on 2008-01-27
HI my name is APU, aka Yellow INdian and you may remember me from shows like the Simpsons lol

anyway, i have an X1950pro but i cant get any of the drivers to work, the restricted drivers in the manager give me the blackscreen of death when i restart my pc so i dont want to do that again.

i have updated UBuntu and i cant get desktop effects to work. x1950 pro is a top mid range card. resolution is at 800x600.. and i have a 22'' TFT, (1680x1050) wide

any ideas, im new to UBuntu so bare with me.

'THank you come again'

[IMG]http://img247.imageshack.us/img247/6848/500pxapunahasapeemapetinn2.png[/IMG]

---

### Post by Ub1476 on 2008-01-27
Maybe the new drivers from ATI will work better for you? Note that video playback does not work when using Compiz with those (you would have to disable it when watching movies), and they are buggy, but getting better every month. [Envy]("http://albertomilone.com/nvidia_scripts1.html") can download and configure them for you. To install Envy, download the .deb package for Ubuntu 7.10 and install it. Launch Envy in the terminal by typing:

```
envy -g
```

Remember to remove any previous installed drivers before Envy install those from ATIs website.

---

### Post by yellowindian on 2008-01-27
i get this message, and it says failed to install..

[IMG]http://img251.imageshack.us/img251/5829/screenshotko5.png[/IMG]

---

### Post by 00arthuryu on 2008-01-27
that says put in the CD to me :lolflag:
but i find that envy doesn't work with my ex-ati cards
if you install ati drivers via the official method then all is well (for me anyway)

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
and follow the instructions EXACTLY
If you have gutsy that is..

I installed my X1950PRO and X1300 via this method

I hope this helps!
Arthy

---

### Post by yellowindian on 2008-01-27
> **00arthuryu said:**
> that says put in the CD to me :lolflag:
but i find that envy doesn't work with my ex-ati cards
if you install ati drivers via the official method then all is well (for me anyway)

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
and follow the instructions EXACTLY
If you have gutsy that is..

I installed my X1950PRO and X1300 via this method

I hope this helps!
Arthy

was that method 1 or 2 ???

im stuck on this :

sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy

where do i put the downloaded file? what directory?

---

### Post by 00arthuryu on 2008-01-27
the second method, don't do the first one
i forgot to mention that in the first post sorry.

if you're running firefox, then the file generally downloads to your desktop
in which case, before you do
```

sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy

```
type
```

cd /home/<yourusername>/Desktop

```

remember the capital D, linux is case sensitive

hopes this helps
Arthy

---

### Post by yellowindian on 2008-01-27
i did what you said below

sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy

**but i got this message back :**

sh: Can't open ati-driver-installer-8-01-x86.x86_64.run

---

### Post by yellowindian on 2008-01-27
problems........ arghhhhhhh

```
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 195: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-inst
```all.xg7790

---

### Post by 00arthuryu on 2008-01-28
i donno what you did there to have an output like that
but please ensure you are root before hand
```

sudo su

```

---

