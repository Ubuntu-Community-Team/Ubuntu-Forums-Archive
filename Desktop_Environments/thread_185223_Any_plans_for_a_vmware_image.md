---
title: "Any plans for a vmware image?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by roger6106 on 2006-05-31
Are there plans to release a vmware image of Ubuntu? That would be very useful for me.

---

### Post by rcarring on 2006-05-31
On VMware's site their browser-appliance is Breezy. The hard file unwraps to 1GB, the zip is over 200mb. A clean installed hard file for Dapper was nearly 2.5GB and as a result I have, for now, abandoned my project of creating a Dapper image.

---

### Post by garyng on 2006-05-31
you can DIY.

use qemu-image to create the "VMWare disk" and install ubuntu there then run vmplayer/vmserver using it.

---

### Post by rcarring on 2006-05-31
In my case I downloaded the vmplayer image and then used a clean install process to wipe the scsi virtual hard disk.

---

### Post by roger6106 on 2006-05-31
[QUOTE=garyng]you can DIY.

use qemu-image to create the "VMWare disk" and install ubuntu there then run vmplayer/vmserver using it.[/QUOTE]

Is qemu-image available for Windows? Where can I get it?

---

### Post by rcarring on 2006-05-31
I thought qemu was only linux and mac, I'll stand corrected if it isnt. Best method for windows is to install the 30 day trial of vmware, and create your image there, back it up and once vmware workstation expires you still have the hard file.

---

### Post by garyng on 2006-05-31
[QUOTE=roger6106]Is qemu-image available for Windows? Where can I get it?[/QUOTE]

I have no idea, check the qemu site. I just used qemu-image on linux to create the file and copy it to windows, just boot(the ISO image, of whatever distro you want) as usual.

---

### Post by roger6106 on 2006-05-31
[QUOTE=rcarring]I thought qemu was only linux and mac, I'll stand corrected if it isnt. Best method for windows is to install the 30 day trial of vmware, and create your image there, back it up and once vmware workstation expires you still have the hard file.[/QUOTE]

I'll try that. I just found [qemu for windows]("http://www.h7.dion.ne.jp/~qemu-win/"), but using the 30day trial sounds easier.

---

### Post by Toxicity999 on 2006-05-31
[http://www.h7.dion.ne.jp/~qemu-win/](http://www.h7.dion.ne.jp/~qemu-win/)

There surely is a windows version. But realistically the VMware workstation trial mentioned would be better for you. If you want to try that anyway.

---

### Post by garyng on 2006-05-31
[QUOTE=rcarring]I thought qemu was only linux and mac, I'll stand corrected if it isnt. Best method for windows is to install the 30 day trial of vmware, and create your image there, back it up and once vmware workstation expires you still have the hard file.[/QUOTE]

qemu can run on windows, just that the windows installer is a bit lagging (0.7 instead of 0.8) and I forget if qemu-image which support vmware disk image is already in there or not.

---

### Post by paddy1978 on 2006-05-31
This site ([http://www.easyvmx.com/]("http://www.easyvmx.com/")) is worth checking out. You can create the various files needed for a virtual machine online then just download the whole thing as a .zip file!

With this you only need to have VMware Player installed...

---

### Post by Toxicity999 on 2006-05-31
Nice paddy, I was just thinking it's rather stupid to get Qemu, which is the same thing as VMware in essence only to create a VMware image... a program ofr doing it alone is waaaaay better in that respect.

---

### Post by EuroCity on 2006-05-31
The best and most up-to-date way of running Qemu on Windows is the excellent frontend [*Qemu Manager*](http://www.davereyn.co.uk/index.htm).

Qemu is much better on the x86 platform (both Windows and Linux); sadly, on the PPC, it is way too slow (emulating x86: unusably slow, one could say!) or unfinished (see emulating another PPC, for example a PPC Linux distro from within OS X).

Anyway, there are also some other frontends, for example the excellent [*Q*](http://www.kberg.ch/q) for Mac OS X.

Other frontends for Qemu are listed on this [FreeOSZoo](http://www.oszoo.org/download.php) page: BTW, why still no Linux Qemu GUI frontend available in Ubuntu...?

---

### Post by roger6106 on 2006-05-31
[QUOTE=paddy1978]This site ([http://www.easyvmx.com/]("http://www.easyvmx.com/")) is worth checking out. You can create the various files needed for a virtual machine online then just download the whole thing as a .zip file!

With this you only need to have VMware Player installed...[/QUOTE]

I'm currently installing the release candidate using this version.

---

### Post by rcarring on 2006-05-31
[QUOTE=paddy1978]This site ([http://www.easyvmx.com/]("http://www.easyvmx.com/")) is worth checking out. You can create the various files needed for a virtual machine online then just download the whole thing as a .zip file!

With this you only need to have VMware Player installed...[/QUOTE]

That's pretty good!

No need to install VMWare trial edition now.

---

### Post by jalonsom on 2006-05-31
Why do you need qemu?
VMware Server is free...

I'd either use VMware Server for a server setup or easyvmx for a single machine setup.

---

