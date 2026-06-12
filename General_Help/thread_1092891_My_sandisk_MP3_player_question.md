---
title: "My sandisk MP3 player question"
date: 2009-03-10
forum: General Help
---

### Post by jras20 on 2009-03-10
How come I can see my files that I put in with windows Vista only in Windows Vista and XP, but if I view it in Ubuntu 8.04 it won't show those files?  I can write to the mp3 player and view them in Ubuntu, but the files that I put in using Ubuntu I can not view them in windows.  What do I do?

---

### Post by ridetheteapot on 2009-03-10
Most likey the usb mode is set to automatic. That means it will use MTP is available, otherwise if will default to MSC. MTP support is limited on linux (if you really want to try libmtp is a start, but doesn't support all devices that use mtp).
You will not see the files put on your I-zune from one mode while in the other. The easy answer in to consolidate all your file to the commonly supported msc mode. Basicly throw you player on the windows box and copy move all the files onto the computer, delete them from you zunepod. Now switch to msc mode in the system settings and put them all back on.

Remember to always unmount (or safely remove in windows) you msc devices before you unplug them.

---

### Post by Nano_ext3 on 2009-03-10
Yes, I had issues with this and my Sansdisk.  Trust me, linux or not MSC is the way to go, you want it to appear as a detachable hard drive.

See this :

[http://www.zolved.com/synapse/view_content/6125/Understanding_the_two_USB_modes_--_MSC_and_MTP_--_on_Sandisk](http://www.zolved.com/synapse/view_content/6125/Understanding_the_two_USB_modes_--_MSC_and_MTP_--_on_Sandisk)

Cheers,

-Nano

---

### Post by jras20 on 2009-03-11
Thanks for the reply, but it still gives me the problem.  I might also say that even on my sandisk 2gb flash card does the same thing.  The only diffrents windows Vista wants to format the card???  I'm not going to do that.  I think Windows XP will see the data off of the card.  But nothing from Vista.

---

### Post by ridetheteapot on 2009-03-11
You have attempted to remove all the data put on the device with mtp?
I mean make sure it is formated vfat(i cant really see this being the problem), and does vista want to format it to vfat also? What model is the mp3 player? If it is old like the e series have you updated the firmware?
I guess if you flash card does the same thing there is something weird going on. I have a sansa fuze but no vista machine to try it on

---

### Post by jras20 on 2009-03-11
> **ridetheteapot said:**
> You have attempted to remove all the data put on the device with mtp?
I mean make sure it is formated vfat(i cant really see this being the problem), and does vista want to format it to vfat also? What model is the mp3 player? If it is old like the e series have you updated the firmware?
I guess if you flash card does the same thing there is something weird going on. I have a sansa fuze but no vista machine to try it on

I'll re-look at the formating thanks, I'll see if I can fix it.

---

### Post by jras20 on 2009-03-11
Strange for some reason Vista started reading what I put in from Ubuntu.  Wonder if it took a re-start to get it to run it under MSC?  Thats strange.  I havn't tested it out on XP yet but I'll do it soon.

---

