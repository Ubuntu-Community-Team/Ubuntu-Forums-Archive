---
title: "WinXP folder links"
date: 2005-05-18
forum: Desktop Environments
---

### Post by pja on 2005-05-18
Hi!
I have just replaced Kubutu with the real Ubutu and am having some minor problems with "the real thing".  My PC has two disk drives: WinXP on hda1 and Umbutu on hdb1.  I would like to make a link to the WinXP "My Documents" folder on the Umbutu desk top.

The WinXP drive is mounted at start-up and is accessible.  I have managed to get a link to the drive but can't get one to any of the directories because they are write protected.

Any help or suggestions would be greatfully appreciated.

By the way, Ubuntu is really getting there; for the first time in the three years I have been playing with Linux, here is a distribution that is nearly as good as Windows (there is no Linux driver for my Canon LBP-1210 laser printer and no Linux equivalent to MyInfo outliner).

Regards,
Peter  :???:

---

### Post by Ali_Baba on 2005-05-18
You can change permissions with chmod command. 
"chmod -R a+w /your mount folder/" this gives all users write access to your mount folder and to all folders under it also. Hope this helps :)

---

### Post by Olli on 2005-05-18
[QUOTE=pja]Hi!
I have just replaced Kubutu with the real Ubutu and am having some minor problems with "the real thing".  My PC has two disk drives: WinXP on hda1 and Umbutu on hdb1.  I would like to make a link to the WinXP "My Documents" folder on the Umbutu desk top.

The WinXP drive is mounted at start-up and is accessible.  I have managed to get a link to the drive but can't get one to any of the directories because they are write protected.

Any help or suggestions would be greatfully appreciated.

<clip>
[/QUOTE]

That WinXP drive is accessible should mean that you can *read* its all subdirectories.
Another thing is that you cannot *write* to ntfs partitions. There are some experimental programmes that may allow writing but their use is discouraged as the probability to mess the partition is very large. 
Access and rights to Windows partitions are defined in your /etc/fstab file.
(for example 

/dev/hda1  /windows/C  ntfs  ro,users,gid=users,umask=0002,nls=iso8859-15 0 0

)

---

### Post by pja on 2005-05-18
[QUOTE=Olli]That WinXP drive is accessible should mean that you can *read* its all subdirectories.
Another thing is that you cannot *write* to ntfs partitions. There are some experimental programmes that may allow writing but their use is discouraged as the probability to mess the partition is very large. 
Access and rights to Windows partitions are defined in your /etc/fstab file.
(for example 

/dev/hda1  /windows/C  ntfs  ro,users,gid=users,umask=0002,nls=iso8859-15 0 0

)[/QUOTE]
 Alli BaBa and Olli,
Thanks for the response.  I have tried 'making a link' when logged-on as 'root' but as Olli says, the WinXP drive is write protected.
There must be a simple way of creating a desktop link - **You can do it with Kubuntu!** but not Ubuntu it seems.
Regards,
Peter

---

### Post by jkndrkn on 2005-05-18
A dirty way that I have used is to open your NTFS directory in a file browser, then drag the folder you want to the taskbar. This will create a taskbar button that acts as a link. You can then drag the new taskbar button to the desktop. The link is not a linux style link, it will only function in the context of clicking on it on the desktop.

Hope this helps.

---

### Post by pja on 2005-05-19
[QUOTE=jkndrkn]A dirty way that I have used is to open your NTFS directory in a file browser, then drag the folder you want to the taskbar. This will create a taskbar button that acts as a link. You can then drag the new taskbar button to the desktop. The link is not a linux style link, it will only function in the context of clicking on it on the desktop.

Hope this helps.[/QUOTE]
 jkndrkn,

**THANKS** That's done the trick.  It might not be pretty but it works just fine.

Thanks,

Peter

---

