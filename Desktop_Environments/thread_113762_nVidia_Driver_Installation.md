---
title: "nVidia Driver Installation"
date: 2006-01-07
forum: Desktop Environments
---

### Post by megabytez on 2006-01-07
The nvidia driver installation requires the kernel source code and I am unable to download it (no internet). Which package in Ubuntu (single cd install) has the kernel source code? If the single-cd doesnt have it, I have the Fedora Core 4 (4 cd).

---

### Post by akiro.yamamoto on 2006-01-07
Use Synaptic to install the build-essential and linux-kernel-headers...
Hopefilly this should do the trick..
For the full kernel source you will need internet access...

---

### Post by Gowator on 2006-01-07
[QUOTE=akiro.yamamoto]Use Synaptic to install the build-essential and linux-kernel-headers...
Hopefilly this should do the trick..
For the full kernel source you will need internet access...[/QUOTE]
But what they mean is you don't need the full source .. only the kernel headers.  
If you have synaptic just search for linux-headers

if not you can install

```
apt-get install linux-headers-'uname -a' 
```
(presuming you have set a root password)

---

### Post by akiro.yamamoto on 2006-01-07
If you really need the source kernel...
[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/)
However I would try to download the nvidia drivers from the repositories and install those instead...

---

### Post by megabytez on 2006-01-07
I can only download through MS Windows and write to a CD.

Isnt there anywhere I can get a RPM package with the kernel source?

---

### Post by akiro.yamamoto on 2006-01-07
The link in my previous post is to the ubuntu repository with the kernel source.
Save the kernel .deb file to a cd. Then install the package in ubuntu..
sudo dpkg -i the_kernel_souce.deb
Done.....
Have you tried installing only the headers.....
As far as I know that is all that you need. The headers provide the required info for the nvidia drivers to be built. The kernel source is usually only required if you need/want to create a custom kernel.
However some distributions do not provide the headers separately so you HAVE to install the entire kernel source.... although you may never need it..
In ubuntu (I have done this) you really only have to install the build essential package as well as the kernel-headers package to be able to build software from source code, both of these packages are available on your install CD.
Hope this helps...

---

### Post by akiro.yamamoto on 2006-01-07
The kernel source is also available in tar.gz format.
The same format that Linus provides.

---

### Post by akiro.yamamoto on 2006-01-07
Paste this link into your browser window...
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=breezy&release=all&keywords=nvidia&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=breezy&release=all&keywords=nvidia&sourceid=mozilla-search)
Now you should be able to download nvidia drivers for your system.
If your using a slightly older card use the nvidia-legacy drivers...

---

### Post by akiro.yamamoto on 2006-01-07
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
That is the website to search for the packages that you need.....

---

### Post by megabytez on 2006-01-07
Which files should I use from that website u gave me? I have a GeForce FX 
5700LE which are supported by the latest nVidia Windows Forceware drivers.

During installation using the drivers from [www.nvidia.com](www.nvidia.com) (after installing the Linux-headers packages) I get an error message.

"Unable to load kernel module 'nvidia.ko'. This is most likely because the kernel module was built using the wrong kernel source files. Please make sure that you have installed the kernel source file for your kernel and it is properly configured. e.g. In a red-hat system, you would need the package kernel-source.

If you are sure you have the correct kernel source, please specify the path."

EDIT: I have a Pentium 4 3.0GHz Prescott

Maybe I have to download a new kernel and get headers of the same version?
Is Linux-686-smp a kernel (version 2.6.12.16.1) and if so where can I get headers for it (cant find them)

---

### Post by mo_x on 2006-01-07
There are many threads on installing the nvidia driver. Please search on the forum.

---

### Post by megabytez on 2006-01-07
When I try to install with the Linux-headers installed, I get an error saying:

Unable to load kernel module 'nvidia.ko'. This is most likely because the kernel module was built using wrong kernel source files. Please make sure that you have installed the correct source file for your kernel and it is properly configured.

e.g. red-hat users would install the package: kernel-source

If you are sure that you have the correct kernel source, please specify the path.


now what?

---

### Post by Gowator on 2006-01-08
[QUOTE=megabytez]When I try to install with the Linux-headers installed, I get an error saying:

Unable to load kernel module 'nvidia.ko'. This is most likely because the kernel module was built using wrong kernel source files. Please make sure that you have installed the correct source file for your kernel and it is properly configured.

e.g. red-hat users would install the package: kernel-source

If you are sure that you have the correct kernel source, please specify the path.


now what?[/QUOTE]


Yes this will be because you ignored my post
> 
apt-get install linux-headers-'uname -a' 

and instead you have installed the unmodified kernel which is not the same as the ubuntu one which is what is returned if you type
uname -r.

> Isnt there anywhere I can get a RPM package with the kernel source?
My line above would have got the .deb for you from the DVD/CD and isntalled it but you seem determined to try and find this on the web as a .rpm which you will never find since no-one is going to package an Ubuntu kernel as an RPM ???

Also the line I have above will only work if you have set a root password as I vbeleive it would be morally wrong of me to help anyone who is still running the Ubuntu default install with ALL:ALL in sudoers which is just a invitation for script kiddies...

---

