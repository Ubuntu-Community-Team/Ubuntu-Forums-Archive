---
title: "Can anyone help me to get the microphone to work?"
date: 2008-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mike.pham on 2008-08-04
i'm using Dell XPS M1330 and I really need to get the microphone to work because I need skype to get my business done.

Can anyone help me.

Thanks alot

Mike

---

### Post by muadnu on 2008-08-04
I have a Vostro 1400 and I'm assuming there's a chance your microphone is the same as mine. In my case it actually works OBO, you just have to set the microphone and volume settings right. See this post [http://ubuntuforums.org/showpost.php?p=4623159&postcount=5]("http://ubuntuforums.org/showpost.php?p=4623159&postcount=5").

And by the way, be sure to go to the Skype options and uncheck the "Allow Skype to set my sounds levels" option (or something like that).

---

### Post by mike.pham on 2008-08-04
okay, i'll try. 
Thanks for your help

---

### Post by antiOST on 2008-08-04
Hi

I think muadnu is on the right track, setting the volume level worked when I got my M1330.

also be sure to check out known issues with M1330 and ubuntu:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Known_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Known_Issues)

Which includes fixes for "Capture Volume Low with External Microphone" and "Built-in Digital Microphone Does Not Work (next to webcam)"

-Kim

---

### Post by mike.pham on 2008-08-04
but then I tried and I couldn't install it. It said dependencies problems. What should I do??



Selecting previously deselected package linux-backports-modules-2.6.22-14-generic.
(Reading database ... 121909 files and directories currently installed.)
Preparing to replace linux-backports-modules-2.6.22-14-generic 2.6.22-14.50 (using linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386.deb) ...
Unpacking replacement linux-backports-modules-2.6.22-14-generic ...
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.22-14-generic:
 linux-backports-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not installed.
dpkg: error processing linux-backports-modules-2.6.22-14-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-backports-modules-2.6.22-14-generic

---

### Post by antiOST on 2008-08-05
Sorry, these problems are out of my league, I'm just a newbie

I haven't tried the microphone next to the webcam, I solved my problem, by adjusting the volume as already suggested and using an externally microphone plugged into the front.

I did try to download the package from dell and just doubleclicked it and the package installer popped up and installed without problems...but I don't get any sound either. 
I am not able to set digital input source to digital mic 1 :-(

I also got curious, so I have tried a bunch of workarounds I found on various forums but still no luck..

Please let me know if you find af solution.

-Kim

---

### Post by muadnu on 2008-08-05
> **mike.pham said:**
> but then I tried and I couldn't install it. It said dependencies problems. What should I do??


A couple of questions mike.pham...

First, what version of Ubuntu are you using? And 32 or 64 bit?

Second, did you try just setting the volume settings correctly, without trying to install the Dell package? As it says in the Dell link, it seems like the mic didn't work on the M1330 on Gutsy. But it might work on Hardy, and as I said in my case (a Vostro 1400 which is the same hardware as the Inspiron 1420n which appears listed as mic not working in Gutsy) it works OBO in Hardy.

Third, what version of the linux kernel are you using? If you don't know, simply type 'uname -r' (without the quotes) in a terminal and post the result. I'm guessing you're are using a kernel more recent than 2.6.22-14, and that might be causing the dependency problem when you try to install the Dell package.

---

