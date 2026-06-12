---
title: "Howto: ATI 8.42.3- + AIGLX (no XGL)"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by proxess on 2007-11-23
[COLOR="Red"]This guide is based on other guides around there, but this one is nicely put together.[/COLOR]
[COLOR="Green"]PS: I wrote this on a PC with an Nvidia Card. My laptop uses ATI.[/COLOR]

First we remove all the crap installed from the Repos
```
sudo apt-get remove fglrx-amdcccle fglrx-kernel-2.6.22-14-generic xorg-driver-fglrx xserver-xgl
```

Now we get all the crap we need for building the debian package
```
sudo apt-get install module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base linux-headers-generic
```

Then we get the Drivers
```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run
```

Now we make it executable
```
chmod +x ati-driver-installer-8.42.3-x86.x86_64.run
```

So now we build the package
```
sudo ln -sf bash /bin/sh
./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

This is how we install them: either double click the generated deb packages or
```
sudo dpkg -i xorg-driver-fglrx_*_i386.deb
sudo dpkg -i fglrx-kernel-source_*_i386.deb
sudo dpkg -i fglrx-amdcccle_*_i386.deb
sudo dpkg -i xorg-driver-fglrx-dev_*_i386.deb
```

We don't want any hidden mess do we?
```
sudo rm /usr/src/fglrx-kernel*.deb
```

Lets make this baby role!
```
sudo m-a update
sudo m-a prepare
sudo m-a build fglrx
sudo m-a install fglrx
```

Compiz must know that your drivers now support AIGLX
```
sudo gedit /usr/bin/compiz
	WHITELIST=”nvidia intel ati fglrx radeon i810&#8243;
```

Now restart X
```
Ctrl+Alt+Backspace
```


There. Enjoy a directly rendered desktop for all your [COLOR="White"]wants[/COLOR] needs on ZSNES and Compiz and the likes.

---

### Post by gonzolono on 2007-11-24
thanks for solving part of my problem. I can now watch dvds using vlc which wasn´t happening before. However, I still cannot use the desktop effects.

Using:
ati radeon x1300
intel pentium 4 
Gigabyte 915G motherboard (GA-81915G pro)
gutsy

glrxinfo now comes up with this:
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Also:
 the ati control centre refuses to run (double click all you like and nothing happens)
and amarok also refuses to run

any suggestions?

Ben

---

### Post by gonzolono on 2007-11-24
ok so I followed the unofficial ati driver wiki and have solved the issue of libGL.so.1 
and now:
ati control centre works
amarok works
BUT desktop effects only works on one quarter of the screen (the rest is black)

is this because my Relisys TL766 monitor&#347; resolution is not good enough to support it?

any thoughts would be very welcome

Ben

---

### Post by proxess on 2008-01-27
monitor resolution isn't a problem i don't think. I can attach my xorg.conf if interested. (its bassed on my nvidia xorg.conf with modifications :D)

---

### Post by pimbeto on 2008-02-03
I followed the guide and as soon as I did the last step (restart X), I logged in and a blank white screen came up and that was it. Any ideas? 

I'm using Gutsy Gibbon on Toshiba A210-MS5 with Radeon X1200. 

Thanks.

---

### Post by proxess on 2008-04-22
Here's the xorg.conf

---

### Post by boyce1 on 2008-04-22
Hey, im a bit of a newbie at linux, so don't rage at me :)

can you explain exactly what this tutorial does? i have an ATI card, and am finding it very difficult to enable compizfusion and AWN. 

Basically, i have installed XGL several times, but whenever i try to log in on Gnome there is no desktop, just a blank pale pink screen. My computer then reboots back into the login mode, where i am forced to login as fail-safe mode and remove XGL.

sorry for ranting on a bit, but does what your saying in this thread fix my problem? thanks.

---

### Post by proxess on 2008-04-25
well with this install you don't need xgl. It uses AIGLX. Thus you get AWN and Compiz-Fusion along with all j00 pr0n.

---

