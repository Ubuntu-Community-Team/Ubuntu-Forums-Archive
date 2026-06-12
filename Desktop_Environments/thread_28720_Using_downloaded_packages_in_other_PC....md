---
title: "Using downloaded packages in other PC..."
date: 2005-04-21
forum: Desktop Environments
---

### Post by Rodrigo on 2005-04-21
Can I use the packages I donwload for my Kubuntu Box, burn them to a cd, or copy them to a usb memory, and install those same packages in another friend computer (with no internet connection)?

---

### Post by gunnyman on 2005-04-21
sure
you just need to add the device to the apt sources.list
No idea how to do that with a USB stick.
Might be better to burn him a cd.

---

### Post by siebzehn on 2005-04-21
[QUOTE=gunnyman]sure
you just need to add the device to the apt sources.list
No idea how to do that with a USB stick.
Might be better to burn him a cd.[/QUOTE]


There's another way,  just copy the packages to your usb stick and then install them on your friend's computer by typing

dpkg -i package-name


You can find the packages you downloaded to your box  in:

/var/cache/apt/archives/

---

### Post by Juergen on 2005-04-21
You need to create a 'Packages.gz' first, e.g.
```
dpkg-scanpackages work-dir /dev/null | gzip > Packages.gz
```Then copy Packages.gz and your work-dir wherever you want.

A cd you have to add with 'apt-cd add' to your friend's sources.lst, for a USB-stick you need to create a 'file:' entry manually.

---

### Post by siebzehn on 2005-04-21
[QUOTE=Juergen]You need to create a 'Packages.gz' first, e.g.
```
dpkg-scanpackages work-dir /dev/null | gzip > Packages.gz
```Then copy Packages.gz and your work-dir wherever you want.

A cd you have to add with 'apt-cd add' to your friend's sources.lst, for a USB-stick you need to create a 'file:' entry manually.[/QUOTE]


I guess this is the "right" way, but why not just install them with  dpkg -i ?

---

### Post by Juergen on 2005-04-21
Perhaps his friend likes Synaptic? 
And/or perhaps he doesn't want all packages - then you'd have to deal with the dependencies manually.

---

### Post by Rodrigo on 2005-04-21
Thank you all for your help!  :grin:

I have just one more question... 
      Can I copy all the files in /var/cache/apt/archives to my friends pc and run apt-get update or upgrade?  (or Im being too lazy haha)  :?

---

### Post by siebzehn on 2005-04-21
[QUOTE=Rodrigo]Thank you all for your help!  :grin:

I have just one more question... 
      Can I copy all the files in /var/cache/apt/archives to my friends pc and run apt-get update or upgrade or something ?  :???:[/QUOTE]
 With my method you can't because the packages will not be included in the sources.list

With the other method nothing would happen really, unless the packages are newer versions of packages already installed in your friend's box.  The thing is if you want to install a NEW package you have to tell that to the machine, apt won't install new software by itself unless is needed by another package and you run apt-get dist-upgrade

---

### Post by fdoving on 2005-04-21
[QUOTE=Rodrigo]Thank you all for your help!  :grin:

I have just one more question... 
      Can I copy all the files in /var/cache/apt/archives to my friends pc and run apt-get update or upgrade?  (or Im being too lazy haha)  :?[/QUOTE]
 not without an internet connecction as far as i know.. /var/cache/apt/archives is just a "cache" for the downloaded packages. apt-get update updates everything from the sources.list file.

I think the best solution for you, is to either do as explained in the other posts for a cd.
Or, add a file entry.. this way:

edit /etc/apt/sources.list and an entry looking something like the example below, of course with modifications to fit your usbsticks mountpoint.

Example: 'deb file:/media/usbstick/ubuntu/ ./'

This exampel expects to find a ubuntu folder on the usbstick, which is mounted on /media/usbstick. Inside the ubuntu folder it expects to find a Packages.gz file.

To generate the Packages.gz file run:
'dpkg-scanpackages work-dir /dev/null | gzip > Packages.gz'

inside ubuntu/ on the usbstick you can have multiple sub directories which all can contain packages. dpkg-scanpackages will find them.

Hope this helps somehow.

- Frode

---

### Post by Rodrigo on 2005-04-21
[QUOTE=siebzehn]With my method you can't because the packages will not be included in the sources.list

With the other method nothing would happen really, unless the packages are newer versions of packages already installed in your friend's box.  The thing is if you want to install a NEW package you have to tell that to the machine, apt won't install new software by itself unless is needed by another package and you run apt-get dist-upgrade[/QUOTE]

THANKS!

---

### Post by siebzehn on 2005-04-21
[QUOTE=Rodrigo]THANKS![/QUOTE]

Anytime

---

