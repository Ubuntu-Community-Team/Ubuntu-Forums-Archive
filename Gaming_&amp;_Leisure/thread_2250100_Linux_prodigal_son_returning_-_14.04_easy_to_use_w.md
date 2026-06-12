---
title: "Linux prodigal son returning - 14.04 easy to use with Steam?"
date: 2014-10-26
forum: Gaming &amp; Leisure
---

### Post by 9littlebees on 2014-10-26
Hi all, I used Linux as a secondary OS to Win7 a few years ago, and ended up getting rid of it.  Long story short, I am coming back, and am trying to decide which distro to use.

I will be using Linux for everything other than multimedia and hardcore gaming.  That said, I would like to use Steam on my Linux OS, so this is where I need some advice.

When I last used Linux, I was using Xubuntu (12.04 if memory serves), which I liked a lot.  I'd prefer to use the newer 14.04, but it doens't look like Steam doesn't always play nicely with newer releases than 12.04.

So my question is, would using installing and using Steam be an easy process on 14.04?  I have an i5 2500k, 16GB RAM & GTX 760, installing Linux onto its own 240GB SSD.

---

### Post by skompier on 2014-10-26
I'm using Steam under Ubuntu 14.04 and have had no issues.

---

### Post by oldrocker99 on 2014-10-26
It works for me in 14.10, since it was beta. How did you install Steam? I would recommend downloading it from steampowered.com, and then installing it thus:
```
cd [path to steam_latest.deb]
sudo dpkg -i steam_latest.deb
```
This will give you an error message, which you fix with the next command:
```
sudo apt-get -f install
```

Also, of course, make sure your video drivers are up-to-date.
This is how I install Steam and I have had no problems at all running the client.

---

### Post by DanglingPointer on 2014-10-26
Another option, would be just to stick to 12.04.5.  I'm currently using it and have no problems whatsoever.  I probably won't switch until the kernels between LTS's diverge for a good length of time.

12.04.5 has the exact same kernel as 14.04 until Feb 2015 at least; with both using the 3.13 Linux Kernel.  14.04 is scheduled to switch to 3.16 in Feb.  12.04.5 could also switch to 3.16 if some vulnerability or use-case issue turns up.

Here are the Kernel release charts... 12.04 and 14.04 Kernel Support charts are two-thirds down the webpage.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by pqwoerituytrueiwoq on 2014-10-26
i don't think sticking with 12.04 is that viable when OP has a GTX 700 series
i would imaging installing 14.04 from alive session may be a issue with the drivers on the iso
i know with my GTX 600 chip it is good enough to install but that is it, now 14.10 should have a decent chance 
assuming the drivers are close to what is in the xorg edgers ppa for 14.04 which are actually useable (except it is unstable with my GPU's softmod OC that works perfect with the nvidia driver blob)
if you are installing from the mini/alt iso this really does not matter as there is no GUI to have issues with drivers

---

### Post by sffvba[e0rt on 2014-10-26
I have had no issues whatsoever with Ubuntu 14.04 or any of the flavours in regards to steam.  Currently running Ubuntu Gnome 14.10 and it was also a simple matter of ***"sudo apt-get install steam"*** (and for the record I am using a GTX770)

---

### Post by DanglingPointer on 2014-10-27
> **pqwoerituytrueiwoq said:**
> i don't think sticking with 12.04 is that viable when OP has a GTX 700 series

Why would it be a problem when the Kernels are exactly the same?

I've got an R9-290X which has even worse support than Nvidia and it works fine during installation.

---

### Post by dannyboy79 on 2014-10-27
> **DanglingPointer said:**
> Why would it be a problem when the Kernels are exactly the same?

I've got an R9-290X which has even worse support than Nvidia and it works fine during installation.
kernels are not the exact same between 12.04 and 14.04, unless you're telling me that 12.04 uses the 3.13 kernel? I know that 14.10 uses kernel 3.16. (which actually I'm running also, it's easy to add 3.16 kernel to 14.04)

to the OP, if i were you I would install Xubuntu 14.04.1, that's what I run and I have a GTX 760. I use Nvidia binary driver 343.22 but it's up to you weather you want to run the repo nvidia driver or nvidia's website driver. I will also point out that i've been seeing many people run into this error, "OpenGL GLX context is not using direct rendering, which may cause performance problems." and I forget whether it's important to install steam before or after you install the proprietary nvidia driver but if you install the nvidia driver from their website ensure that you also install it's 32bit library files because steam is still only 32bit.

The arch wiki has some very helpful info for reference [https://wiki.archlinux.org/index.php/steam](https://wiki.archlinux.org/index.php/steam)

---

### Post by DanglingPointer on 2014-10-27
Hi danny, my post #4 above...

In a nutshell, the latest official 12.04.5 is kernel 3.13 which is what I'm running.  The Kernel release chart is also pasted above.  14.04 won't officially have 3.16 until Feb next year.  (Obviously it doesn't stop anyone from upgrading unofficially all the way to 3.18 if they want)

---

### Post by pqwoerituytrueiwoq on 2014-10-28
> **dannyboy79 said:**
> kernels are not the exact same between 12.04 and 14.04, unless you're telling me that 12.04 uses the 3.13 kernel? I know that 14.10 uses kernel 3.16. (which actually I'm running also, it's easy to add 3.16 kernel to 14.04)

to the OP, if i were you I would install Xubuntu 14.04.1, that's what I run and I have a GTX 760. I use Nvidia binary driver 343.22 but it's up to you weather you want to run the repo nvidia driver or nvidia's website driver. I will also point out that i've been seeing many people run into this error, "OpenGL GLX context is not using direct rendering, which may cause performance problems." and I forget whether it's important to install steam before or after you install the proprietary nvidia driver but if you install the nvidia driver from their website ensure that you also install it's 32bit library files because steam is still only 32bit.

The arch wiki has some very helpful info for reference [https://wiki.archlinux.org/index.php/steam](https://wiki.archlinux.org/index.php/steam)

speaking of 3.16 on trusty, any luck getting nvidia 340.46 to work with 3.16.6? using the x org edgers ppa here 
i with on 3.16.3, not .5 and .6
have not tried .4
it fails to compile and does not make the log file it tells you to look in
seems to fail the gcc version check, which i solved and it still does not work
using mainline kernels

---

### Post by dannyboy79 on 2014-10-28
> **pqwoerituytrueiwoq said:**
> speaking of 3.16 on trusty, any luck getting nvidia 340.46 to work with 3.16.6? using the x org edgers ppa here 
i with on 3.16.3, not .5 and .6
have not tried .4
it fails to compile and does not make the log file it tells you to look in
seems to fail the gcc version check, which i solved and it still does not work
using mainline kernelsI don't use Xorg-edgers, I use the 343.22 binary from the Nvidia website and it's working fine with Utopic mainline 3.16 kernel. Not sure on the version number of the kernel though. And actually after I installed kernel 3.16 in  Xubuntu 14.04 I didn't even have to reinstall the Nvidia driver, it just worked so DKMS worked like it's suppose to.

---

### Post by pqwoerituytrueiwoq on 2014-10-28
> **dannyboy79 said:**
> I don't use Xorg-edgers, I use the 343.22 binary from the Nvidia website and it's working fine with Utopic mainline 3.16 kernel. Not sure on the version number of the kernel though. And actually after I installed kernel 3.16 in  Xubuntu 14.04 I didn't even have to reinstall the Nvidia driver, it just worked so DKMS worked like it's suppose to.
can you run uname -r and tell me if you are using newer than 3.16.3-031603-generic which does work with nvidia just like the other older kernels
edit
for some reason a thing fails to compile nvidia related but nvidia works, so...

---

