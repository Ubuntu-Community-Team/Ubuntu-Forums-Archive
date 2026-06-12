---
title: "is there a 9.04 netbook remix ISO???????"
date: 2009-04-28
forum: General Help
---

### Post by jhchadwell on 2009-04-28
I have an aspire one that for some awful reason will not boot from usb.  in fact it will not boot at all with a usb fd plugged in.  So given that I have an external dvd drive is there a UNR iso out there as opposed to the .img?  Or maybe better, is there a way to convert the img to iso.

---

### Post by mikewhatever on 2009-04-28
Why? An .img is just another image file, same as .iso.

---

### Post by bruceschaller on 2009-04-28
I had the same problem. Does it keep booting into XP, no matter what you are doing?

I followed these steps to get it to work. 

1st, check and see if your usb stick isn't being recognized as a removable device or usb in the boot menu.  

next go to the hard drive menu (in the bios) with your usb plugged in. It may show up there.  

Then, I think you can set it to 1st device in the hddisk menu. (Try the autodetect)

Go back to boot order, and select your usb device.

and now it should work.

Another tip, you may want to reformat your flash as a fat 16 or fat 32 file system.  Seems easiest for the bios to pick up on as an external hddisk.

---

### Post by anjilslaire on 2009-04-28
Agreed. I installed 8.10 via usb onto an Acer Aspire One a few months ago. That system boots from usb flash drives just fine, assuming you've connfigured the bios corectly and your usb stick is comparible.

---

### Post by jhchadwell on 2009-04-28
Bios is good.  It actually hangs at Bios with any usb fd plugged in, doesn't even begin to boot grub.  there must be some sort of conflict, its odd.  in bios usb is supposed to boot first.  I had this issue when i put 8.10 on, but i just bought a usb cd/dvd and all was well.  Maybe it is a compatibility issue, didnt realize that...  looked into it and it is a good poss.  will try a different one tomorrow.  Which one did you use anjilslaire?  Will try to format it now too. 

[I]46 Minutes Ago 10:16 PM
mikewhatever 	
Re: is there a 9.04 netbook remix ISO???????
Why? An .img is just another image file, same as .iso. [/I]

does that mean i can just burn the img to a disk as if it were an iso and go????

---

### Post by bruceschaller on 2009-04-28
Try hard drive boot 1st.  The best way to get an image to flash is Unetbootin.  Last I did it, it actually (the flash) appeared to be a hddisk...

I guess you could also try a different flash (if you have one) or a network install...but it is probably more effort than it's worth.  Sorry if I didn't help ya much.  Good luck!  Try resetting bios setting to factory default, maybe reflash bios?  that might straighten you out too...

---

### Post by jhchadwell on 2009-04-28
I reformatted the usb.  it was fat16 so i figured i would try fat32.  Still could not get past initial Bios splash screen with stick plugged in, no F2, no F12, just hangs there.  Did some research, apparently this stick sucks.  Will try a new one tommorow.

---

### Post by jhchadwell on 2009-04-29
Okay problem solved.  I don't knwo where in my noodle this info got lost, but...  i think i once knew that you can't just copy the image, you have to write it using an image writer... did that all is well am actually installing as we speak.  By the way 9.04 rocks!

---

### Post by timcredible on 2009-04-29
for a bootable liveflash of ubuntu, the easiest way is just use system->administration->usb startup disk creator

---

### Post by anjilslaire on 2009-04-30
Yes, but the NBR .img is NOT an ISO. As Jhchadwell learned,you need to write it to the usb stick with the ubuntu image writer
[https://wiki.ubuntu.com/UNR#Easy%20(graphical)%20Way](https://wiki.ubuntu.com/UNR#Easy%20(graphical)%20Way)

Glad you got it sorted :)

BTW, I use a SanDisk Cruzer Micro 4gig

---

