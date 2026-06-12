---
title: "About version and administrator user??"
date: 2012-10-28
forum: Desktop Environments
---

### Post by omar ahmad on 2012-10-28
HI , 
i want to ask if there is a 32 bit version and 64 version in kubuntu and how can i know my version?
 because i want to increase my RAM from 2 G to 4G and i dont know if iam going to use all 4 G or not??

and i want to delete a wallpaper in usr/share/wallpaper
but i got this message( Access denid to - file  path- )
how can i make it?
thanks

---

### Post by mparillo on 2012-10-28
Could it be wallpapers instead of wallpaper? Or you need to sudo?

mparillo@ubuntu:/usr/share$ cd wallpapers
mparillo@ubuntu:/usr/share/wallpapers$ ls
Ariya  kde-default.png  stripes.png  stripes.png.desktop
mparillo@ubuntu:/usr/share/wallpapers$ rm kde-default.png
rm: cannot remove `kde-default.png': Permission denied
mparillo@ubuntu:/usr/share/wallpapers$ sudo rm kde-default.png
[sudo] password for mparillo: 
mparillo@ubuntu:/usr/share/wallpapers$ ls
Ariya  stripes.png  stripes.png.desktop

---

### Post by drmrgd on 2012-10-28
> **omar ahmad said:**
> HI , 
i want to ask if there is a 32 bit version and 64 version in kubuntu and how can i know my version?
 because i want to increase my RAM from 2 G to 4G and i dont know if iam going to use all 4 G or not??

and i want to delete a wallpaper in usr/share/wallpaper
but i got this message( Access denid to - file  path- )
how can i make it?
thanks

To the first question, if you run from the terminal:

```
uname -a
```

That will give you all the info about your install, including the Linux kernel version and the architecture.  If you see 'x86_64' you're running 64-bit.

---

### Post by AlexDudko on 2012-10-28
> uname -m
if the output will be x86_64 then it's a 64-bit version.

---

### Post by deadflowr on 2012-10-28
Making any changes to system files or folders, you'll need root privileges. Since Ubuntu disables root by default, you use the sudo command to grant you temporary escalated privileges.
So for example, using the command 
rm /usr/share/wallpaper/wallpaper.png, will result in permission denied. Where as, adding sudo in front will give you the rights to rm(remove) the file.

---

### Post by omar ahmad on 2012-10-29
for the command

uname -a
the output 
Linux kubuntu 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:32:50 UTC 2012 i686 i686 i386 GNU/Linux
so it is 32 right?
any extra inf. should i know from the output?

for the secound one

sudo rm /usr/share/wallpapers/Ariya
the output
rm: cannot remove `/usr/share/wallpapers/Ariya': Is a directory
so how can i make it ?
and any way to remove it via Dolphin program ? as easy as WINDOWN (Rt .click - delete)
thanks

---

### Post by PaulW2U on 2012-10-29
> **omar ahmad said:**
> 
uname -a
the output 
Linux kubuntu 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:32:50 UTC 2012 i686 i686 i386 GNU/Linux
so it is 32 right?


Yes, i686 means you have a 32-bit OS.

> **omar ahmad said:**
> 
and any way to remove it via Dolphin program ? as easy as WINDOWN (Rt .click - delete)


Yes, press **Alt-F2**, type **kdesudo dolphin**, navigate to directory and delete it.

Take care to delete only the directory you want to delete as you will have root privileges which will allow you to delete just about anything.

---

### Post by omar ahmad on 2012-10-29
> **PaulW2U said:**
> Yes, i686 means you have a 32-bit OS.

so can the 32 see the 4G ram??

> **PaulW2U said:**
> Yes, press **Alt-F2**, type **kdesudo dolphin**, navigate to directory and delete it.

Take care to delete only the directory you want to delete as you will have root privileges which will allow you to delete just about anything.

i made it but any way to continuo with root access or i have to type **kdesudo dolphin **everytime??

thanks

---

### Post by AlexDudko on 2012-10-29
> **omar ahmad said:**
> so can the 32 see the 4G ram??


thanks

Yes, if you install pae kernel.

---

### Post by drmrgd on 2012-10-29
> **omar ahmad said:**
> so can the 32 see the 4G ram??



i made it but any way to continuo with root access or i have to type **kdesudo dolphin **everytime??

thanks

To your second question, running 'kdesudo' Dolphin launches Dolphin with root privileges.  It is the equivalent of using sudo in the command line.  So, as long as you have the Dolphin window opened with kdesude, you'll have root access and will be able to do whatever you like (so be careful!).  When you close the window, that will end root access in Dolphin, and if you need to get it again, you'll have to issue 'kdesudo Dolphin' again.

Incidentally, the error you got when you tried to remove the directory from the command line was because you need to add '-r' for directories since it is a recursive deletion.  The command should have been:

```
sudo rm -r /usr/share/wallpapers/Ariya
```

---

### Post by omar ahmad on 2012-10-31
> **drmrgd said:**
> To your second question, running 'kdesudo' Dolphin launches Dolphin with root privileges.  It is the equivalent of using sudo in the command line.  So, as long as you have the Dolphin window opened with kdesude, you'll have root access and will be able to do whatever you like (so be careful!).  When you close the window, that will end root access in Dolphin, and if you need to get it again, you'll have to issue 'kdesudo Dolphin' again.

Incidentally, the error you got when you tried to remove the directory from the command line was because you need to add '-r' for directories since it is a recursive deletion.  The command should have been:

```
sudo rm -r /usr/share/wallpapers/Ariya
```
  
thanks for your help

---

