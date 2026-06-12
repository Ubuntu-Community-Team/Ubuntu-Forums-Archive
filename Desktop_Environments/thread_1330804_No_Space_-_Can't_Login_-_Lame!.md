---
title: "No Space - Can't Login - Lame!"
date: 2009-11-18
forum: Desktop Environments
---

### Post by marcon00 on 2009-11-18
I found it very weird and very un-practical,i didn't notice that i run out of space on my Home Directory, and i rebooted.I tried loggin in, i couldn't .. it said my home directory was inaccessible or there was no space (which was the case) , i tried to login as root - but i forgot that you got to enable that before. I guess i could access termianl by shutting down GUI right ? with a combo of keys, ALT+ F12 ? nevertheless , i did't do that.

I was stuck :\ had to boot to windows, move bit of files to be able to login. (lame)

Why there isn't such option to reserve like couple of Mb of space , just to prevent such a situation ?  


PS: it's more of a complain / suggestion thread :\ and i still want answers :p

---

### Post by Zorael on 2009-11-18
If you boot to recovery mode, there's an option to clear the apt cache which should free up some space on your root drive.

If your home directory is on another partition, and it's full, I think the only way is to login textually, via recovery mode if necessary, and move/delete some files. I think both GNOME and KDE keeps the trash (recycling bin contents) in ~/.local/share/Trash, for instance.

---

### Post by kayosiii on 2009-11-18
Purhaps the desktop should reserve enough room so that a user can at least log in graphically to clean out some space.

---

### Post by marcon00 on 2009-11-19
> **Zorael said:**
> If you boot to recovery mode, there's an option to clear the apt cache which should free up some space on your root drive.

If your home directory is on another partition, and it's full, I think the only way is to login textually, via recovery mode if necessary, and move/delete some files. I think both GNOME and KDE keeps the trash (recycling bin contents) in ~/.local/share/Trash, for instance.

I'm aware that there are many ways to get things done, but what it happened to a new user or someone that just uses Linux?

[QUOTE=kayosiii]
Purhaps the desktop should reserve enough room so that a user can at least log in graphically to clean out some space. [/QUOTE]

That's what i believe too !

---

### Post by wilee-nilee on 2009-11-19
So is this the programs fault or is it the users responsibility to monitor how full the HD is getting, all you have to do is applications-accessories-disc usage analyzer. Did you dual boot  and make the partitions to small or is this a wubi install?

---

### Post by marcon00 on 2009-11-19
> **wilee-nilee said:**
> So is this the programs fault or is it the users responsibility to monitor how full the HD is getting, all you have to do is applications-accessories-disc usage analyzer. Did you dual boot  and make the partitions to small or is this a wubi install?

let's say the partition is too small , if you consider 190GB home directory too small. I was downloading, and didn't notice that i run out of space, and rebooted. It's not the issue, i solved it easily before posting even, the whole idea is that this is lame that i couldn't login! a normal use that,lets say, switched from Windowd to Linux will not know what to do. Therefore , this shouldn't happen and should be avoided, because it's the small things that differ.

---

### Post by ScottMinster on 2009-11-19
> **marcon00 said:**
> let's say the partition is too small , if you consider 190GB home directory too small. I was downloading, and didn't notice that i run out of space, and rebooted. It's not the issue, i solved it easily before posting even, the whole idea is that this is lame that i couldn't login! a normal use that,lets say, switched from Windowd to Linux will not know what to do. Therefore , this shouldn't happen and should be avoided, because it's the small things that differ.

When you start to login, after you enter or select your username, but before you enter your password, you should be able to select what desktop environment to use under the "sessions" selector.  In Karmic, that seems to be at the bottom of the screen.  There are two options "Failsafe Gnome" and "xterm" that would probably allow you to login even if your home directory's partition is completely full and allow you to delete files.  I don't know exactly how failsafe Gnome is different, but it sounds like it should work.

I know that xterm will just give you a single terminal window, which you can use to manage files.  Of course, with xterm, you have to know how to use command like 'cd', 'mv', 'rm', and likely others like 'du', so it's not quite for beginners.

It probably would be nice if there was some (graphical) utility that could be run if the main DE detects there's no space that allows the user to manage their files more easily.

---

### Post by wilee-nilee on 2009-11-19
> **marcon00 said:**
> let's say the partition is too small , if you consider 190GB home directory too small. I was downloading, and didn't notice that i run out of space, and rebooted. It's not the issue, i solved it easily before posting even, the whole idea is that this is lame that i couldn't login! a normal use that,lets say, switched from Windowd to Linux will not know what to do. Therefore , this shouldn't happen and should be avoided, because it's the small things that differ.

I think most everybody that is here to get help and help others wants to see everybody have the best experience. I have never seen this sort of issue addressed on here before in this context. If you fixed it even before you posted then maybe it should have been a learning experience rather then a reason to complain. Personally if this had happened to me I would say to myself now that wasn't a very bright move.

Why don't you write a program or script that does just what you want, and use it. If you have spent any time on this forum using windows as a example even in a hypothetical circumstance will hardly be supported be anybody. It is your responsibility to monitor your computer. I bet this doesn't happen again to you, now you know. This is free software that allows you do many things without worrying about being hacked, infected and requires very little maintenance. 

I suspect you were downloading something that didn't have a file size that the computer recognized like a P2P, if you tried to install a program that was larger then the HD space it would tell you that there is no room. If it wasn't a P2P download that filled up your computer, as a windows user you should be aware of temporary files this would probably be the culprit. The temp files are made when you use your computer, and are hardly as obtrusive as on a MS system.

---

### Post by marcon00 on 2009-11-19
> **ScottMinster said:**
> When you start to login, after you enter or select your username, but before you enter your password, you should be able to select what desktop environment to use under the "sessions" selector.  In Karmic, that seems to be at the bottom of the screen.  There are two options "Failsafe Gnome" and "xterm" that would probably allow you to login even if your home directory's partition is completely full and allow you to delete files.  I don't know exactly how failsafe Gnome is different, but it sounds like it should work.

I know that xterm will just give you a single terminal window, which you can use to manage files.  Of course, with xterm, you have to know how to use command like 'cd', 'mv', 'rm', and likely others like 'du', so it's not quite for beginners.

It probably would be nice if there was some (graphical) utility that could be run if the main DE detects there's no space that allows the user to manage their files more easily.


I tried all the sessions :) didn't work. i still got the same error

---

### Post by marcon00 on 2009-11-19
> **wilee-nilee said:**
> I think most everybody that is here to get help and help others wants to see everybody have the best experience. I have never seen this sort of issue addressed on here before in this context. If you fixed it even before you posted then maybe it should have been a learning experience rather then a reason to complain. Personally if this had happened to me I would say to myself now that wasn't a very bright move.

Why don't you write a program or script that does just what you want, and use it. If you have spent any time on this forum using windows as a example even in a hypothetical circumstance will hardly be supported be anybody. It is your responsibility to monitor your computer. I bet this doesn't happen again to you, now you know. This is free software that allows you do many things without worrying about being hacked, infected and requires very little maintenance. 

I suspect you were downloading something that didn't have a file size that the computer recognized like a P2P, if you tried to install a program that was larger then the HD space it would tell you that there is no room. If it wasn't a P2P download that filled up your computer, as a windows user you should be aware of temporary files this would probably be the culprit. The temp files are made when you use your computer, and are hardly as obtrusive as on a MS system.

I barely use windows,but there are things that simply need windows.
My post here is tended to educate other users as i found it weird to come across such an issue, and maybe get someone to do something about it. So you don't have to come here and give me lectures especially about what Linux stands for or how i'm supposed to use my OS - no matter to what i'm refering :) Feel free to be supportive,otherwise you are more than welcome not to follow up this thread.

---

### Post by cariboo on 2009-11-19
This thread doesn't seem to be accomplishing anything, therefore it is closed.

---

