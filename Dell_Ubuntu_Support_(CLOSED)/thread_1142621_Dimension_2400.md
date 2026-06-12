---
title: "Dimension 2400"
date: 2009-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Teh Fail on 2009-04-29
Whenever I login on ubuntu, kubuntu or xubuntu, all without conpiz, after a little bit of loading after login the screen freezes. The screen doesn't go blank it just shows what was there before. I have tried multiple times on ubuntu kubuntu znd xubuntu and the same thing happens on them all. This may be unrelated, but whenever it boots it says that the check for the floppy drive has failed. My floppy drive has been removed.

---

### Post by abn91c on 2009-04-29
try disabling the FDD controller in the BIOS, the PC is still looking for it, if you are using 8.10 or going to 9.04 is best to completely remove compiz with you 2400. By the way I just installed this card on my 2400 it works well in windows xp [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4471396&CatId=319](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4471396&CatId=319)

---

### Post by Teh Fail on 2009-04-29
Could you remind me how to do that, please?
 
p.s. i have BIOS version A02
 
And if it helps, when it freezes both the caps lock and scroll lock keys on the keyboard flash

---

### Post by abn91c on 2009-04-29
> **Teh Fail said:**
> Could you remind me how to do that, please?
 
p.s. i have BIOS version A02
 
And if it helps, when it freezes both the caps lock and scroll lock keys on the keyboard flash
reboot press f2, then in the bios( i have a05) there is a drive configuration line, press enter and change diskette drive a to Not Installed, use the - or + key to do it th press ESC twice, make sure "save changes" is highlighted then enter to reboot

---

### Post by Teh Fail on 2009-04-30
bump : need help about the freezing

---

### Post by Teh Fail on 2009-04-30
Solved it myself.  Apparently, all you need to do is turn off Fast Boot in the BIOS. Thanks to everyone for their help.:KS

---

