---
title: "bootup trouble"
date: 2008-12-05
forum: General Help
---

### Post by smithdrumm on 2008-12-05
To anyone who can help,

I just received the new 8.10 version in the mail, but upon bootup, it either gets to the desktop, flashes 1-4 mouse pointers and stops , or it gets to the black boot screen with the small cd icon and stops. Can someone please help me?

---

### Post by Peter09 on 2008-12-05
What is the spec of your computer?

---

### Post by ChrisBookwood on 2008-12-05
I have no idea what could be wrong.
But if you are up to installing the system, you could try to simply click install, when the first menu comes up (where you also can choose to start ubuntu up with no changes to your harddrive, or simple boot from the harddisk).
It could be something with your rams, being old or something, and therefor having troubles with the live disc, since it uses the rams very heavily indeed.

Don't hang me up on this, though.

---

### Post by smithdrumm on 2008-12-05
> **Peter09 said:**
> What is the spec of your computer?
The external drive is a SimpleTech 320 GB (USB 2.0). Please let me know any other information you may need. Computer is an emachines T3302, 160GB hard drive, 2 GB RAM.

---

### Post by ash_nug on 2008-12-05
Why does it matter what your external drive is?

Its like telling us what brand of mouse you have. 

Unless you installed Ubuntu on your external for some reason, which I wouldnt....

---

### Post by mrvertigo on 2008-12-06
> **smithdrumm said:**
> To anyone who can help,

I just received the new 8.10 version in the mail, but upon bootup, it either gets to the desktop, flashes 1-4 mouse pointers and stops , or it gets to the black boot screen with the small cd icon and stops. Can someone please help me?

Smithdrum, you contacted me by email yesterday on this issue, i feel as it would be more helpfull to others if we were to solve it here.

in addition to the basic questions ask here and in our emails, i feel the need to ask if the video card your using is factory stock or if it was put in aftermarket? do you know what kind of card you have?

---

### Post by smithdrumm on 2008-12-15
Hi mrvertigo,
Thanks for trying to help. I really appreciate it! My video card is a VIA/S3G UniChrome Pro, and it was factory installed. Hope this information helps you to try and solve my problem. Thanks again for all your help! Sorry it took so long to reply.

                                     Best,

                                     David Smith (smithdrumm)

---

### Post by falcon61102 on 2008-12-15
When you first get to the LiveCD boot menu, try pressing F4 and selecting one of the alternate options for starting up.  

It may be that there is a driver conflict that needs to be resolved and by starting in a Safe or Recovery Mode you can work around that issue.

---

### Post by spcwingo on 2008-12-15
I've had problems with s3 video cards before.  Try to input xforcevesa on bootup.  To do that, when it shows the screen asking if you want to start, install, etc. highlight start and press F6.  Then just type xforcevesa.  It may work...it may not.  Let us know how it turns out for you.

---

### Post by mrvertigo on 2008-12-16
this issue was resolved, in part, i took a house visit to smithdrumm to see just exactly what we were dealing with. turns out that his origional windows boot loader was replaced by grub (no big) but he then installed ubuntu 8.10 from within windows using wubi, for whatever reason wubi did not add his linux partitions to the altered boot menu and grub was no longer present. we fixed this issue by uninstalling the wubi version of ubuntu and installing ubuntu on his external drive, we used ubuntu 7.04 because i had a copy and i knew it was compatable, the plan was to go the upgrade path. this meathod has worked for me in the past with issues like his. During upgrade I attempted showing off synaptic and in opening synaptic i believe i broke apt. he now gets a 404 error during any further upgrade attempts regardless of what server is used.

 > **smithdrumm said:**
> To anyone who can help,

I just received the new 8.10 version in the mail, but upon bootup, it either gets to the desktop, flashes 1-4 mouse pointers and stops , or it gets to the black boot screen with the small cd icon and stops. Can someone please help me?

---

