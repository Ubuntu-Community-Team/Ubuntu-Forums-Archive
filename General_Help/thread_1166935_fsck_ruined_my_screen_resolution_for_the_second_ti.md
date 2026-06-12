---
title: "fsck ruined my screen resolution for the second time"
date: 2009-05-22
forum: General Help
---

### Post by molom on 2009-05-22
I was running Ubuntu 8.10 perfectly with a 9800gt using the nvidia drivers on 1680x1050 resolution until it came into an ultra small resolution 800x600. I didn't know what it was but I knew it was the first time I let the forced HDD check before startup. I used the Ubuntu LiveCD and surprisingly it came up with that same resolution even though before this HDD check it had the perfect resolution during the LiveCD. I've tried fixing xorg in an unimaginable amount of ways, but it didn't work.

I waited for Ubuntu 9.04 and it gave me the correct resolution, and installed it. The LiveCD for 9.04 used the perfect resolution. I let this forced check occur again and it came with the very poor resolution AGAIN, and I can't manage to fix it. The LiveCD also uses the same resolution.

What has this forced check done? If it affects the LiveCD session also, what could be the issue. What has this forced HDD check done to my computer?

---

### Post by molom on 2009-05-22
*bump*

I really need help!

---

### Post by KhurramM on 2009-05-22
Just copy paste the xorg.conf from the LiveCd session onto the installed system.

Hope this helps.

---

### Post by molom on 2009-05-22
Thanks for your help.

I've tried it before and I've tried it again. It didn't work. 

What makes me curious is that the LiveCD now shows that poor resolution like my installed ubuntu. How could fsck done on my HDD change the resolution of a livecd, which doesn't use my installed settings? Does fsck somehow store some special memory or something (Very much doubt it did something to my bios)?

I have re-installed xorg, xserver and even gnome-desktop and it didn't change anything. When I use the nvidia drivers the resolution becomes even smaller than the 800x600 produced when using the vesa drivers.

Does anyone have a solution? This is one of the strangest bugs I have ever seen.

---

### Post by molom on 2009-05-23
Ok, I pulled the plug out from the HDD and the Ubuntu Livecd still gives me that poor resolution. So I assumed fsck somehow touched my bios settings, so I flashed the bios and updated it, still doesn't work. What could be the problem? I just can't understand it.

Can anyone help me out?

---

### Post by abhilashm86 on 2009-05-23
There is an application of resolution, go to system->preferances->system resolution. You have detect resolution or you can change it, what is your problem all about??

---

### Post by molom on 2009-05-23
> **abhilashm86 said:**
> There is an application of resolution, go to system->preferances->system resolution. You have detect resolution or you can change it, what is your problem all about??

The problem is that my proper resolution (1680x1050) is not available in the display setting. My resolution is now 800x600 using vesa and 640x480 when using nvidia. This happened to me after a forced hdd scan on ubuntu 8.10 and now it has happened on 9.04.

---

### Post by lisati on 2009-05-23
I don't see how fsck could mess up your screen resolution settings unless the relevant config files are stored on a dodgy area of the disk.

---

### Post by molom on 2009-05-23
> **lisati said:**
> I don't see how fsck could mess up your screen resolution settings unless the relevant config files are stored on a dodgy area of the disk.

I don't know what it is, because as I said, now my (Not CD-RW) same Ubuntu Livecd uses that horrible resolution when it would use the right resolution before I installed 9.04. Is there anyway that ram has some permanent memory stored, bios has been changed or anything else. It can't be a hard drive problem...

---

### Post by molom on 2009-05-25
I thought that I would get some working advice here considering this is a huge community, but someone gave me the answer on another very small forum. I unplugged my DVI cable from my monitor and computer and then removed the power cable from the monitor. plugging it all back in again, it returned back to 1680x1050. I can't understand how fsck could do such an awkward thing...

---

