---
title: "dell inspiron 530 (help)"
date: 2007-12-30
forum: Dell  Ubuntu Support
---

### Post by odm on 2007-12-30
i have a dell inspiron 530 with the intel core2duo 6650 with windows vista home premuim. in my primary hd i have vista of course and  in my second hd i have linux my problem is that wen i installed linux i only gave linux about 15gb of the 300gb well now my hd wont show up in vista so i dont know what went wrong can anyone help???

---

### Post by puzzledinmn on 2008-01-24
I'm not sure about the wording on your question but 15GB is plenty for Ubuntu unless you have large amounts of data to add.  Vista cannot use your Ubuntu drive, but when you are in Ubuntu 7.10 you can right click the Vista drive(or partition if you meant that), select mount and then use your Vista files.  Add more details if this is not what you meant.

---

### Post by jetole on 2008-01-28
Yeah I am not sure about your wording either but to me it sounds like you cannot run Vi$ta at all. Basically like someone who wants a dual boot system without fully understanding what it means and who is now sitting around saying either "d0h", "fsck", "wtf?", or "where did that go?". If you have uttered any of these terms recently then next time your computer boots, right after the BIOS has loaded you will see a booting menu. If your Vi$ta is on this list then select Vi$ta. If you do not then you may have blindly deleted your Vi$ta partition and recreated it during setup. 

](*,) With any operating system, you cannot just change the partition layout of an active operating system partition and expect the OS to know what happened. If you changed the start of partition then you can't even expect to find the OS let alone expect it know why if you do ever rearrange it back to normality. 

The last thing for you to consider, if you know that you handled the partitioning properly, is perhaps Ubuntu did not recognize the Vi$ta partition and although it is untouched and should function properly, there may just be no entry for it in Grub, which is your boot loader now on the MBR.

Arthur: Normality? We can talk about normality until the cows come home.
Ford: What is normal?
Trillian: What is home?
Zaphod: What're cows?  ;)

---

