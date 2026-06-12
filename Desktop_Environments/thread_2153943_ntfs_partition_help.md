---
title: "ntfs partition help"
date: 2013-06-12
forum: Desktop Environments
---

### Post by mreyna16 on 2013-06-12
i dont know if this is the right forum to ask so please excuse me if it aint....

i have an ntfs partition that is being shared with both ubuntu 13.04 and windows 8 but ive noticed that every now and then my files dont show up... for example, i created a libre office file with some information and saved it on my ntfs partition thats visible on both ubuntu and windows but when i was in windows the file wasnt there. ill be honest and say that i have not gone back into ubuntu and see if its visible using ubuntu but im more than sure i saved it right... any reason for this? all help is appreciated, thanks!

---

### Post by oldfred on 2013-06-12
Did you turn off fast boot or the always hibernated "feature" of Windows 8?

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by mreyna16 on 2013-06-13
I have downloaded r studio, a program to scan the ntfs drive and see if it has bad files and ive also turned off fast boot... come to think about it some of my files such as pictures got messed up somehow in the process of moving them back and forth because of me having problems with that ntfs partition and reformatting it... hopefully using r studio will recover my files and at the same time fix my partition if it is messed up.

---

