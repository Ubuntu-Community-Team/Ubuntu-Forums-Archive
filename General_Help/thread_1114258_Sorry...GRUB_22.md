---
title: "Sorry...GRUB 22"
date: 2009-04-02
forum: General Help
---

### Post by its_david on 2009-04-02
Hello. Sorry, your going to have to excuse my complete ignorance in anything Ubuntu and GRUB (I don't even know what GRUB is :S) related. 
Long story short. A friend Installed Ubuntu on my laptop which also had Windows Vista on it. My hard drive was split into two equal parts, but as I use Vista more I felt I needed more space for that OS. I have 160Gb/2 to make 2 80Gb partitions. I wanted 130Gb for vista and 30Gb for Ubuntu). Neither me nor my friend knew what we were doing but I believe we tried to delete the partition (Ubuntu one). After a reset, the logo of the make of the laptop appears but then an error comes up that says "GRUB loading stage1.5" and the "Error 22"
I have checked the other posts such as [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), but it doesn't help (another error message appears after the second code).
One last thing. I have a recovery disc (it came with the laptop and I have used it before...if that makes a difference) but it does not help at all. Problem remains :(
Please, I need help without complicated jargon that will get my computer back to an if not normal, at least usable state.

Thank you. x

---

### Post by ronparent on 2009-04-02
Short answer: when the ubuntu partioion was deledted grub was deleted also (only the grub bootloader was left on your boot drive). So nothing will load.

The next step is dependent on what you want to accomplish. To install a smaller Ubuntu, simply boot the ubuntu live cd and run a custom install leaving room to expand the Vista partition. Or alternatively, if uou don't intend reinstalling ubuntu, use the Vista install disk to restore the Vista master boot record. Someone else will have to direct you for that latter step since I haven't yet done a Vista fix.

---

### Post by d-mart on 2009-04-02
did you use the vista disk manager to partition the drive?  Because if not i would try to use the super grub disk to fix it.  You just need to burn the live and then there is an option to fix windows boot.  The super grub disk fixed this error when i had this problem on xp but i dunno if it will work for vista as i have never had this problem with vista.

---

### Post by its_david on 2009-04-02
I used the Vista disk manager. I'm re-installing Ubuntu so it will take up the whole HD. I really dont know what i'm doing, just playing by ear; so any help would still be appreciated.

---

