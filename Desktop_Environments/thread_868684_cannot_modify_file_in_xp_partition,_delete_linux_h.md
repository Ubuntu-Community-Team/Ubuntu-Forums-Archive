---
title: "cannot modify file in xp partition, delete linux header, login trouble..........."
date: 2008-07-24
forum: Desktop Environments
---

### Post by gilang on 2008-07-24
1.any1 can help me?
i can't modify (delete, rename, replace, etc) any file in windows xp partition anymore....

how could this happen?

i didn't change any setting in my hardy, as i can remember...i just did update my hardy everytime there is a new update....and suddenly, those thing happen....




2. everytime i updated my hardy, there is new version of linux header...is it safe to delete the previous version?
is there any file i can delete after i updated my hardy?
as long as i know, i can just delete the old kernel ([http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/))



3. sometimes, i got trouble when i log into my hardy...
after i fill my username and password, the only i can see is my desktop wallpaper...no panel, no screenlet, no awn...
just wallpaper. the only thing i can do is press ctrl alt backspace to get back to login page. if i did login via filesafe session, it work normal. 

this problem not often happen, but i hope i can fix this too...



thank u to anyone who can fix my problems...

---

### Post by brimlar on 2008-07-24
1)  I've seen this happen when you do an unclean shutdown while in XP -- it flags your XP partition as "in use" and as a result Ubuntu won't let you modify files while that partition is flagged.  Booting up and letting XP take the flag off (often it will ask to check your filesystem in this situation) fixes it.  Just one idea -- I'm not sure if applies to you or not.

2)  When you upgrade Ubuntu and you get new kernels from the update, it is generally safe to delete the older kernels if you want, *if you know what you are doing*, if you don't know what you are doing you can seriously screw up your operating system.

3)  Unsure.

---

### Post by Potatoj316 on 2008-07-24
You have to install a package to allow NTFS support.  Maybe that package got removed, if it worked before.

---

### Post by gilang on 2008-07-26
thank u guys, i'm not sure if i remove the "ntfs package"...

---

