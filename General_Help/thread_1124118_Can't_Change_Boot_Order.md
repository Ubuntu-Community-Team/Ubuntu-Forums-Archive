---
title: "Can't Change Boot Order"
date: 2009-04-13
forum: General Help
---

### Post by Lunx on 2009-04-13
Yesterday I created a couple of bootable flashdrives, but when I decided to test them I find I can no longer change the boot order of my system. Computer is an OEM that once had Windows XP installed and I was able to change the order by hitting shift+F10 on start-up. I had it set to boot from CD/DVD drive if a disc was inserted, otherwise it then gave me the option of which OS I wanted to boot. Not sure if this stuffed up while I still had XP, or if it's something that happened when I installed Ubuntu. I havn't messed with any settings, or tried to change it until yesterday when I discovered hitting the buttons does nothing whatsoever, 'puter just keeps on with startup process and boots Ubuntu normally. Not even sure how I begin to try solving this (do I alter a file in /boot ?), so suggestions as to commands I can try and edits I can make will be gratefully accepted.

---

### Post by Cybie257 on 2009-04-13
Try hitting F12 on BIOS boot up screen.
If the doesn't give you boot options, go into the BIOS (Usually DEL key or F2 as soon as BIOS Info begins to display) and see if you can change the order in there. I'd set the order to the following:

1 - CD/DVD
2 - USB
3 - Hard Drive.

This order would probably work best for your situation. 

Hope this helps. 

-Cybie

---

### Post by Lunx on 2009-04-13
> **Cybie257 said:**
> Try hitting F12 on BIOS boot up screen.
If the doesn't give you boot options, go into the BIOS (Usually DEL key or F2 as soon as BIOS Info begins to display) and see if you can change the order in there. I'd set the order to the following:

1 - CD/DVD
2 - USB
3 - Hard Drive.

This order would probably work best for your situation. 

Hope this helps. 

-Cybie


Thanks for that, managed to get it sorted now and your suggestions were helpful as it's been a while since I've played it there, you refreshed my memory on how to go about it all. Your advice was all the things I was trying to do but not getting anywhere with earlier. Tried it again just now and it seems it is something to do with my keyboard, sometimes hitting keys continuously lets me get into the BIOS settings, then next time I try in exactly same way it won't work for me. 

Anyhow, thanks again, my problem is now all sorted and boot order's been changed (found out the Ubuntu stick I made won't work, but I popped in one I created yesterday with Puppy on it and works a treat!)

---

