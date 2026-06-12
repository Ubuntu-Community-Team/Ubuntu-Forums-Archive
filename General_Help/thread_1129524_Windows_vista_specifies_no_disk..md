---
title: "Windows vista specifies no disk."
date: 2009-04-18
forum: General Help
---

### Post by dragos240 on 2009-04-18
Just so you get it, I am 100% ubuntu, my dad wants to use vista for backup purposes so he can boot into windows if I mess something up. He doesn't know that windows is terrible at that, and that I have all the pc-fixing tools anyone would ever need. Although I'll get in trouble if I don't get vista working again, the error message is:

Title: Windows - No Disk

Msg: 
**Windows Vista Exception Processing Message 0xc0000013**

This happens when I boot up, there is no login screen or anything. Just that message, I had previous experience with this message In xp, it meant that windows couldn't find the main drive, although I forced mounted the vista drive in ubuntu and all the files are still there, perfectly in tact, also, testdisk says that everything is A okay. Can anyone help me at least figure out what's wrong?

---

### Post by jbrown96 on 2009-04-18
I'm not sure if Vista has this same problem, but XP did. If the hard drive is set to SATA or RAID mode, XP won't see the drive. Try to go into your BIOS menu, and set the hard drive to compatibility mode or IDE.


There is a separate forum for Windows related questions. Please post Windows specific questions in there.

---

### Post by dragos240 on 2009-04-18
> **jbrown96 said:**
> I'm not sure if Vista has this same problem, but XP did. If the hard drive is set to SATA or RAID mode, XP won't see the drive. Try to go into your BIOS menu, and set the hard drive to compatibility mode or IDE.


There is a separate forum for Windows related questions. Please post Windows specific questions in there.

Do you mean the "Other OS" forum? If so, it's long gone, and now those questions belong in here.

---

### Post by jbrown96 on 2009-04-18
[Here]("http://ubuntuforums.org/forumdisplay.php?f=170")

---

### Post by dragos240 on 2009-04-18
> **jbrown96 said:**
> [Here]("http://ubuntuforums.org/forumdisplay.php?f=170")

That forum is closed. As I mentioned before. This is the place now to post topics.

---

### Post by fballem on 2009-04-18
> **dragos240 said:**
> Just so you get it, I am 100% ubuntu, my dad wants to use vista for backup purposes so he can boot into windows if I mess something up. He doesn't know that windows is terrible at that, and that I have all the pc-fixing tools anyone would ever need. Although I'll get in trouble if I don't get vista working again, the error message is:

Title: Windows - No Disk

Msg: 
**Windows Vista Exception Processing Message 0xc0000013**

This happens when I boot up, there is no login screen or anything. Just that message, I had previous experience with this message In xp, it meant that windows couldn't find the main drive, although I forced mounted the vista drive in ubuntu and all the files are still there, perfectly in tact, also, testdisk says that everything is A okay. Can anyone help me at least figure out what's wrong?

At one point, I had to restore Vista on my computer and ran into the same issue. I called Microsoft support and they were able to help me. There are some things that you need to do through the Windows command line at the time when you're installing windows.

If you need to restore Windows, then please call Microsoft. I found them most helpful.

---

### Post by linuxisevolution on 2009-04-18
I believe this means your drive letter assignment in Windows is confusing itself. This always left me confumbled.

Although, removing all drives in your computer except C: might work. Then you can use Windows Drive manager or something to permanently assign that drive letter. You can also try changing your boot order in bios.

---

### Post by dragos240 on 2009-04-25
Bump. I am NOT calling microsoft for help.

---

### Post by dragos240 on 2009-04-26
Bump again.

---

