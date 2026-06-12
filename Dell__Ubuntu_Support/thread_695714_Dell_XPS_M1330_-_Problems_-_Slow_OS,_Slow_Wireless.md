---
title: "Dell XPS M1330 - Problems - Slow OS, Slow Wireless."
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by E-Mike on 2008-02-13
I've had a look around and i can't seem to find any fixes.

I Have the Dell XPS M1330, which has the Nvida 128mb 8400M GS, and the Intel Prowireless 3945ABG.

I am using the restricted drivers for both (the ones which come with ubuntu)

I Installed Ubuntu myself and i've looked around and it seems that the Graphics card is slowing the OS, and the drivers for the wireless (ipw3945) don't work properly with WPA Encryption.

I've tried disabling ipv6, that didn't help much, and i've changed my /etc/sysctl.conf. that didn't work either.

I'm fairly new to linux, i have basic knowledge, and i can get things done but i need a little instruction on alot of things to do so unfortunatley.

can anyone help me with these problems? it would be very much appreciated, as i wish to use Ubuntu as my main OS, im trying to move away from the appauling windows. i liked XP more than any other windows, but im sick of it now. 

I'm sorry if this has been solved before but i can't seem to find any solutions.

thanks,
Mike.

---

### Post by notwen on 2008-02-13
The included ipw wireless module is not stable in Gutsy, [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues") is a workaround to blacklist the ipw module and enable the iwl module instead.  Good luck w/ your graphics issues.  =]

---

### Post by sgtbug on 2008-02-13
i am using 3945 too.. it is perfect in my system..

---

### Post by E-Mike on 2008-02-13
Thanks very much for that little fix, that worked great! still need to sort my graphics though :D thanks very much!

---

### Post by notwen on 2008-02-13
Glad that worked for you, there are no issues regarding the nVidia 8400M GS on Dell's Linus wiki, other than issues pertaining to Suspend/Resume.  Do you know whether or not you have enabled Compiz-Fusion by chance?  Your system should run it smoothly anyway, but it may be causing a slowdown graphically if you had the right combination of effects enabled all at once.

---

### Post by E-Mike on 2008-02-13
is it enabled if you have the visual graphics set to normal or extra? i did have it set to normal. i've disabled that now, ill see how it performs... :) thanks

---

### Post by ikey_d on 2008-02-13
DELL has some workarounds on their Linux page... they also have a custom Ubuntu CD image with all the workarounds done by default; it says it's for the 1330n but the hardware is the same so it should work. I'm downloading it now to verify it works with 1330m.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Desktops_and_Notebooks_with_Ubuntu_Desktop_Edition_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Desktops_and_Notebooks_with_Ubuntu_Desktop_Edition_7.10)

---

### Post by E-Mike on 2008-02-14
Thanks for all the help guys, i think i've solved the compiz one aswell!
If you run $gstreamer-properties then you can change the video "plugin" to X Windows System (no xv) and you can use compiz fusion and video playback. i don't think it's slowing the system down either now.

Ubuntu owns!

oh and by the way, does a anyone know why the dell ubuntu disc is a 4 gb dvd, whereas the official disc is only 700mb?

---

### Post by notwen on 2008-02-14
The Ubuntu DVD includes all needed files(it's the whole Ubuntu repository) so in a sense you could install all the default packages available for Ubuntu while off line using this DVD.  The official Ubuntu CD only houses the files/packages needed for the base install.  I personally carry my Ubuntu DVD around w/ me at all times should I not be near a wifi AP and need to install a app/lib/pacakge.  =]

Here's a [link]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/gutsy/release/") to some 'official' Ubuntu DVDs released by Canonical.

---

