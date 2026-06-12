---
title: "Dual monitor hell: using nVidia &amp; ATI in one system."
date: 2005-10-09
forum: Desktop Environments
---

### Post by martijntje on 2005-10-09
I'm having trouble getting hardware acceleration working with both my nVidia and my ATI card. I have succesfully installed and activated the nVidia drivers, but i can't seem to get the ATI driver to install successfully.

Whenever i try to install the xorg-driver-fglrx package, i get an error about a conflicting module. 

> Preconfiguring packages ...
(Database inlezen ... 65916 bestanden en mappen geïnstalleerd.)
Uitpakken van xorg-driver-fglrx (uit .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_amd64.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
dpkg: fout bij afhandelen van /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_amd64.deb (--unpack):
 subproces pre-installation script gaf een foutwaarde 2 terug
Fouten gevonden tijdens behandelen van:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
So, the package won't install successfully. I then tried downloading the drivers myself, from the ati website, but it kept complaining about an 'unauthorized download', or discontinued sessions, and it refused to let me download anything.

I am now using the vesa driver, it works, of course,but it's terribly slow. If i try to watch a movie on it, it uses about 50% CPU, it's really annoying.

I'm at a loss here, i really want to get hardware acceleration up and running for the ATI card. Does anyone have any idea, how to get both packages to run at the same time?

Thanks in advance.

---

### Post by justinchudgar on 2006-10-21
I've got an integrated ATI Xpress 200 and an nVidia PCI card; and, I am having the same problem in that I cannot seem to use binary drivers for both simultaneously. Please advise.

---

### Post by Ocxic on 2006-10-21
from what i can tell, from the error msg is that both drivers are trying to divert the use of "/usr/lib/libGL.so.1" to two different locations, corrisponding to each driver. the system doen't allow a file to be diverted like that scince it will likly cause problems, as both drivers would try to use the same file, at the same time, and interfere with each other.

I don't know a solution for this problem, and i don't know if there is one.
but if you two swaped your cards to have a matched setup it would save from not being able to do this, or buying another vidoe card so you can.
just a suggestion.

---

### Post by CatKiller on 2006-10-21
I've got an nVidia AGP card and an Ati PCI card - no prizes for guessing which one gets the proprietary driver. You can switch from the vesa to the ati driver with no problems. I haven't yet managed to get 3D going on the Ati card, but otherwise the driver is pretty decent.

If you persevere and manage to get it working, I'm sure there are lots of people that would be **very** interested in exactly how.

---

### Post by justinchudgar on 2006-10-25
> If you persevere and manage to get it working, I'm sure there are lots of people that would be very interested in exactly how.

<rant>
I'm sure there would be. I'm just incredibly frustrated that something that I have done for years, certainly since Win2K came out, without thinking twice, without forum crawling, etc, is so damned difficult. I mean, I'm not using Gentoo or trying this on an ancient SparcStation.

RRRRRRR....
</rant>

Sorry.

---

### Post by CatKiller on 2006-10-25
Take it up with nVidia and Ati. It's their fault that their drivers won't get along, after all.

---

### Post by justinchudgar on 2006-10-26
> from what i can tell, from the error msg is that both drivers are trying to divert the use of "/usr/lib/libGL.so.1" to two different locations, corrisponding to each driver. the system doen't allow a file to be diverted like that scince it will likly cause problems, as both drivers would try to use the same file, at the same time, and interfere with each other.

Since they are trying to install their own libs in /usr/libs and then create links from /usr/libs/<OEM-name>, why can't they install their libs directly to their own directories?

Do any other processes need to see the libs?

---

