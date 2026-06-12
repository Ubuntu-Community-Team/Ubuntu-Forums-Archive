---
title: "wanting to get rid of ubuntu"
date: 2007-07-04
forum: Dell  Ubuntu Support
---

### Post by Broderick_G on 2007-07-04
Hey I have a Dell dimension 4600 that has both Ubuntu, and Windows XP. How could I rid ubuntu from my hard drive, without deleting my windows Os?

thanks

---

### Post by stimpack on 2007-07-04
You will need to remove the bootloader. the command is FIXMBR I think it can only be run in recovery console from Windows installation CD.

Then it will boot into windows direct. Just format your ubuntu partition as NTFS.

---

### Post by Workinman57 on 2007-07-04
[LEFT]Try [www.Google.com](www.Google.com) Look for editing the partion table of your drive. Better backup your windows partion as editing the partion table is a risk. Once you have boot sector re-tuned to boot only windows you should be able to delete the partion with Ubuntu and if running W2K or XP you can recover the partion then format it to be used by windows again with the disk manager. You can buy Partion Magic and I belive it will do all the operations for you. You can also boot with your windows cd in W2K or XP and choose the repair option to move boot partion table. But what ever you do Back up your important stuff. This also works in reverse for those who would like to nuke thier windows install. May I ask if you are having some issues with Ubuntu? I have had both Great success and some hair pulling adventures. The forums are a great place to find resolutions to many issues [/LEFT]

---

### Post by Broderick_G on 2007-07-04
thanks

---

### Post by Bothered on 2007-07-04
Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=481046#post2891590").

Note that these instructions assume you have only one hard drive. If you have more than 1, then point 3 may not apply - if you have ubuntu installed on a separate partition to Windows ignore point 3, then when back in Windows reformat the blank space. Remember to back up data before modifying partitions.

As well as losing the Windows master boot record when you installed ubuntu, the install has probably disabled the Dell system restore functionality (if you system had it originally). See [here]("http://www.goodells.net/dellrestore/fixes.htm") for instructions if you want to fix this (use with caution!).

---

### Post by ubuntujonez on 2007-07-04
Let me know how it goes Broderick_G. I have a Dell Dimension 4600 and there are very serious problems with my system and Feisty. I'm going to have to go back to Edgy because I have been fighting with this for days... serious problems with the hardware and the 2.6.20 kernel. I guess I may try going back to the previous stable kernel before reinstalling Edgy.

-jonez

---

### Post by Workinman57 on 2007-07-04
I had to go back to 6.10 also. Dell Laptops C840 and Insprion 8200. If you want to just go back to a lower version you should be able to just boot the cd and pick the current ubuntu Partition format and reinstall old version. Windows Partition should be recognized and added to boot record during the install. As with anything I suggest Remember to "back up anything important to you" 

6.10 is sweet Sound and Display work so much better then any windows OS. But my Display goes bye bye if I use the Nvidia non free drivers. Go figure?

---

### Post by ubuntujonez on 2007-07-04
I just reinstalled 6.10. Works perfectly. I'm happy again. I guess I'll try again when Gutsy (7.10) is released. As soon as I have time, I plan on producing some debugging info so these machines can be usefull again with a future Linux OS.

---

