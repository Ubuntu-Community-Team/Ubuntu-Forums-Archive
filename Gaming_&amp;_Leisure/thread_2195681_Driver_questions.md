---
title: "Driver questions"
date: 2013-12-25
forum: Gaming &amp; Leisure
---

### Post by sjackling on 2013-12-25
I have an asus eah5770. I have no issues building the driver from ATI. What i want to know is if its possible to take my asus specific driver (it worked better than the ones from ati and obviously it was customized for the card) and smart doctor (monitoring tempurature, controlling fan speeds, etc.) and convert it to ubuntu, or would i be better off using the ati driver i assembled and finding a smartdoctor ubuntu equivalent? And if so any suggestions on one? Thanks in advance :D

---

### Post by sjackling on 2013-12-27
UPDATE: I had no trouble building the driver but frankly its garbage. I get a black screen after login, and after a few tries i just removed all the flgrx stuff with the terminal and called it a day. While i would like the card specific drivers and software im beginning to think thats not going to happen so any suggestions on a smartdoctor alternative?

---

### Post by mips on 2013-12-27
Sell it and get a nvidia card. I know I'm not helping but when it comes to linux & ati I have very little faith.

---

### Post by QIII on 2013-12-27
Hello!

I'm not sure what you mean by "building the driver from ATI", since the ATI driver is a proprietary, closed source binary package.  You can install it from the repo, build a .deb from the ATI installer to install it  or install it directly using ATI's installer package.  But you can't build the driver.

You can build the open source Radeon driver if you want I suppose, but I don't know why you'd bother since it is already installed by default when you install Ubuntu.

Could you tell us exactly what you did?

---

### Post by sjackling on 2013-12-28
> **mips said:**
> Sell it and get a nvidia card. I know I'm not helping but when it comes to linux & ati I have very little faith.

mips, i agree completely. I bought my parts as a barebones kit and i have always preferred Nvidia over ATI. Looking into buying a Titan soon :D

---

### Post by sjackling on 2013-12-28
> **QIII said:**
> Hello!

I'm not sure what you mean by "building the driver from ATI", since the ATI driver is a proprietary, closed source binary package.  You can install it from the repo, build a .deb from the ATI installer to install it  or install it directly using ATI's installer package.  But you can't build the driver.

You can build the open source Radeon driver if you want I suppose, but I don't know why you'd bother since it is already installed by default when you install Ubuntu.

Could you tell us exactly what you did?

QIII, i was referring to building the .deb. I installed all the dependencies and built it with no error messages whatsoever, and after rebooting i get a black screen of death after login. Honestly, the card is garbage since even with the drivers from ASUS it still has issues on my win7 install, and they stopped supporting it before half of those issues were resolved. Therefore, i think ill just use the open source driver until i can get my hands on a nice new Nvidia card. Thanks anyways though :D

---

### Post by dannyboy79 on 2013-12-29
have you tried the AMD Catalyst 13.12 driver? I used it with the HD5750 and now the HD7770 black edition. There's nothing to build, you simply run the .run installer file as root.

---

### Post by sjackling on 2013-12-29
> **dannyboy79 said:**
> have you tried the AMD Catalyst 13.12 driver? I used it with the HD5750 and now the HD7770 black edition. There's nothing to build, you simply run the .run installer file as root.

That is the driver im talking about... honestly i think the card is just garbage but ill give that a shot when i get back to my desktop and let you know how it goes

---

### Post by dannyboy79 on 2013-12-30
> **sjackling said:**
> That is the driver im talking about... honestly i think the card is just garbage but ill give that a shot when i get back to my desktop and let you know how it goes

it is paramount that you properly uninstall any previous fglrx driver first. there's a thread that i wrote about my experience with going from the older AMD driver to a newer one, i would suggest reading the last few posts in it because I documented what worked for me

---

### Post by sjackling on 2013-12-30
Heres what happens. In the terminal i type "sudo amd-catalyst-13.12-linux-x86.x86_64.run --Buildpkg Ubuntu/saucy", which builds the .deb files fine, no issues. Then i type "sudo dpkg -i fglrx*.deb" which returns this error (its the only one); "Error! Bad return status for module build on kernel: 3.11.0-14-generic (x86_64) Consult /var/lib/dkms/fglrx/13.251/build/make.log for more information." [ATTACH]249031[/ATTACH] and to me being a noob to linux thats all gibberish :p

---

### Post by R33D3M33R on 2013-12-30
The installer seems to be broken for Ubuntu, read here: [http://phoronix.com/forums/showthread.php?91885-AMD-Catalyst-13-12-GPU-Driver-For-Linux-Released/page3](http://phoronix.com/forums/showthread.php?91885-AMD-Catalyst-13-12-GPU-Driver-For-Linux-Released/page3)
Use the debs i linked in this topic: [http://ubuntuforums.org/showthread.php?t=2194891](http://ubuntuforums.org/showthread.php?t=2194891)

---

### Post by sjackling on 2013-12-31
Well 13.12 wouldnt work for me, so i went to the link of repositories provided by R33D3M33R and downloaded the 13.125 packages... im still a little confused because i double checked and i did download the 13.125 pkg but i have 13.101 installed? but either way its in it works and im happy i don't have to mess around with it anymore... now to go test it with something... like Dolphin!! Thanks to all, im marking this thread as solved :D

---

