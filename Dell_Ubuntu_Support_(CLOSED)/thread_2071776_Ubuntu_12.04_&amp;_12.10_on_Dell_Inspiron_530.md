---
title: "Ubuntu 12.04 &amp; 12.10 on Dell Inspiron 530"
date: 2012-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DomB2012 on 2012-10-16
I have attempted with 12.04 and the upcoming 12.10 to boot Ubuntu from both a USB and CD on a Dell Inspiron 530, to no luck...

When I use either a USB or CD, the purple screen and Ubuntu logo appears with the orange & white dots moving across the screen, but then nothing else materialises. When the CD is being used, the CD stops spinning (as you can hear it) and no progress is made.

I've tried all sorts of settings within the BIOS, to no luck also. Is this a known problem with the Inspiron 530 or other Dell PC's?

If anyone knows a permanent fix, it would be greatly appreciated! :(

---

### Post by gbrainin on 2012-10-16
I have seen a similar problem with my 530 when trying to boot from USB.  The BIOS driver doesn't quite work right, and I've had to use a workaround where I have the PLOP boot manager boot from CD, then use that to boot from USB.  The PLOP boot manager loads enough of a USB driver so that the Ubuntu USB succeeds.

That having been said, I have been able to boot directly from an Ubuntu CD, so you may be having a different problem from mine.

---

### Post by cmcanulty on 2012-10-16
I had the problem on an HP laptop. The solution was to blacklist the wireless and install from ethernet then edit grub. Someone more advanced will have to give details. Worth a try anyway but also very irritating as I have a very common wireless card.

---

### Post by DomB2012 on 2012-10-16
Is the PLOP boot manager something I can easily install to a CD? Is it an ISO image or something? I may give that a try, but I wouldn't want it to succeed, and for me to install Ubuntu to the PC for it to then not boot, if you know what I mean.

Thanks


> **gbrainin said:**
> I have seen a similar problem with my 530 when trying to boot from USB.  The BIOS driver doesn't quite work right, and I've had to use a workaround where I have the PLOP boot manager boot from CD, then use that to boot from USB.  The PLOP boot manager loads enough of a USB driver so that the Ubuntu USB succeeds.

That having been said, I have been able to boot directly from an Ubuntu CD, so you may be having a different problem from mine.

---

### Post by DomB2012 on 2012-10-16
Thanks for the reply. The Inspiron 530 is sadly a Desktop computer which doesn't actually come with a Wireless adaptor of any sorts, so that suggestion won't work sadly.

Thanks 

> **cmcanulty said:**
> I had the problem on an HP laptop. The solution was to blacklist the wireless and install from ethernet then edit grub. Someone more advanced will have to give details. Worth a try anyway but also very irritating as I have a very common wireless card.

---

### Post by gbrainin on 2012-10-17
> **DomB2012 said:**
> Is the PLOP boot manager something I can easily install to a CD? Is it an ISO image or something? I may give that a try, but I wouldn't want it to succeed, and for me to install Ubuntu to the PC for it to then not boot, if you know what I mean.

Thanks

It's been a while, but I recall that the boot manager is an ISO image that's easily burned to a CD.

As for booting from the hard drive after installation, I've been using Ubuntu exclusively since 7.04, and the only problem I've ever had with that was easily solved by switching between RAID and SATA modes in the BIOS.

---

### Post by DomB2012 on 2012-10-17
And so using that boot manager you were talking about which you burn on to a CD, does that just replace the Windows boot manager? If I'm right in saying that...
 
Which mode setting should it be on to work with both Ubuntu and Windows... RAID or SATA? I've changed it once before and it made Windows go a little crazy at first... 
 
Thanks
 
 
> **gbrainin said:**
> It's been a while, but I recall that the boot manager is an ISO image that's easily burned to a CD.
 
As for booting from the hard drive after installation, I've been using Ubuntu exclusively since 7.04, and the only problem I've ever had with that was easily solved by switching between RAID and SATA modes in the BIOS.

---

### Post by gbrainin on 2012-10-17
> **DomB2012 said:**
> And so using that boot manager you were talking about which you burn on to a CD, does that just replace the Windows boot manager? If I'm right in saying that...
 
Which mode setting should it be on to work with both Ubuntu and Windows... RAID or SATA? I've changed it once before and it made Windows go a little crazy at first... 
 
Thanks

The PLOP boot manager boots from the CD, but does not require installation to the hard drive.  It doesn't make any changes to your drive unless you instruct it to.  However, it does let you boot to the USB after it is loaded.

I don't recall which setting (SATA or RAID) Ubuntu wanted, but it was the opposite one from the one that Windows wants.

---

### Post by DomB2012 on 2012-10-18
Oh right. I shall have a look at the PLOP manager once installing Ubuntu 12.10 is completed on various machines I have. Big day!
 
Thanks
 
 
> **gbrainin said:**
> The PLOP boot manager boots from the CD, but does not require installation to the hard drive. It doesn't make any changes to your drive unless you instruct it to. However, it does let you boot to the USB after it is loaded.
 
I don't recall which setting (SATA or RAID) Ubuntu wanted, but it was the opposite one from the one that Windows wants.

---

