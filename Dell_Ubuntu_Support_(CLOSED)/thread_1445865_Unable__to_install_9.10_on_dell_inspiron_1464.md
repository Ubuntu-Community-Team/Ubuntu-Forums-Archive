---
title: "Unable  to install 9.10 on dell inspiron 1464"
date: 2010-04-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anurag chauhan on 2010-04-03
Hi folks,
I have just baught my new laptop dell inspiron 1464 (2GB RAM, i3  processor ). I have alraedy installed vista and is working fine for me. I tried to install ubuntu 9.10. I tried to install from CD. After reboot I select option ubuntu ... then further option comes which asked me to install ubuntu and after selecting that nothing appears ... just a blank screen.
From this CD ubuntu was installed properly in some other laptop.... I followed every step correct but don't know what is the problem.
 
I tried another option ubuntu 8.04 lts from CD.... in this I moved one step ahead ... but when it tried to detect my CDROM.... it asked me that "may be some other modules needed to detect CDROM pl. insert your floppy disk" ... don't know what to do?
 
Some body told me that try 9.10 ubuntu from butable pen drive (with the help of universal installer )... I also did this .. but after making butable I was not able to boot from usb ..as it was saying kernal image is corrupted .. once again a failure

---

### Post by sullenxone on 2010-04-03
when viewing my ubuntu 9.10 on my laptop without installing ive found that if i move my laptop too much that it will freeze up and ill have to force reboot my laptop. this may be a contributer to your problem. another issue that might be, is if youve used the CD for installing on multiple machines, the disk maybe worn out and perhaps you should burn a new one. this is just my theory on the matter though. i doubt your having any internal hardware problems since your laptop is new.

---

### Post by Yvan300 on 2010-04-03
The kernel image being corrupted suggests that the files were not copied properly to the usb. I suggest you use unetbootin to install ubuntu onto your flash drive. It might work this time.

---

### Post by anurag chauhan on 2010-04-04
Hi thanks for replying.... After using unetbootin ... I restart my laptop and boot it from usb drive  ... I found the same blank screen  ... Is there any issue with display screen resolution of  my laptop well I myself doubt that .. I think if this blank screen issue resolves I will be able to install ubuntu properly!!!

---

### Post by Yvan300 on 2010-04-04
Hmmm, this is really strange indeed. Using older version of ubuntu such as 8.04 won't get you far because of the lack of drivers and the current version has a problem installing on your laptop. Ok.... well you can try installing ubuntu by 'trying' it first instead of just clicking 'install ubuntu ' from the cd menu. Also you could try the previous version (jaunty jackalope) and see if the problem exists and as a last resort you could install ubuntu from within windows through wubi. Be warned, i have had some buggy experiences with wubi but that was a long time ago. I hope you get your problem resolved so that you could enjoy ubuntu ):P

---

### Post by airbeku@yahoo.com on 2010-04-05
Hi guys,
I also got the same problem, I tried to follow one of thread from this forum by first tried to install Ubuntu 8.04, then upgraded to 9.04 then 9.10. My new inspiron 1464 failed to read anything from 8.04 cd. 
 
Then, I tried the 9.04 cd but during the installation I always get I/O message. I will try to download buntu 8.04 and 9.04 and I hope the problem will be solved.
 
I hope the failure is due to cd quality only, not from from the incompatibility between inspiron 1464 and UBuntu *sigh*

---

### Post by airbeku@yahoo.com on 2010-04-05
Sorry, I mean I always got I/O error message :P

---

### Post by Yvan300 on 2010-04-05
Sometimes your optical drive may be the cause of the problem. For example i had a friend with a laptop about 2 months old and he had trouble installing ubuntu and windows 7. But when we installed from a flash drive, there were no hiccups. Both installs worked flawlessly. So i suggest you try booting from a flash drive.You got nothing to lose anyway!

---

### Post by kutturuvan on 2010-04-09
I have a similar problem. I finally managed to get it working, but with a low resolution.

I guess there is an issue with the display detection and drivers for Inspiron 1464. So do this to install 9.10:

1. In the boot screen, choose "install" option
2. Before pressing 'enter', press F4  and choose safe graphics mode.
3. Press 'enter' and proceed to install.

The resulting installation will have a low resolution, (mine at 1024x 768) in a wide screen.

Now i'm searching for the solution of this.


Hope this helps.

---

### Post by smferguson on 2010-04-10
fyi, i had the same issues with 9.10 and decided to try the beta. just got 10.04 beta 2 installed on my inspiron 1464. the video works well. took a little to get the wireless drivers installed, but they're up and running now... of course i've no idea if you want to be on the bleading edge. but it looks really good so far. :D

---

### Post by lifetonjoyu on 2010-10-31
Hey,,buddies,,,let me tell you that the 9.10 is not going to work fine with this model of dell.....i also own this laptop and faced the same prblm.....i personally talked to the dell authourities n they told me that this one is specially windows oriented manfactured lappy,,,,so 9.10 is not suitable for it.....,,,,so i hold n installed the 10.04 which they told me supposed to work fine with our dell 14...,,,,and right from the second day of launch of 10.04 i m using ubuntu on my lappy,,,,,not even a single issue i have yet,,,,,,itz totally pleasing,,,,so i suggest everybody to not to mess up with 9.10 n go for 10,04,,,,,,coz i personally faced a headace n was worthless##### go for 10.04 n njoy!!!!!!

---

