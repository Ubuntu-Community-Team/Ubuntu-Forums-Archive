---
title: "can't find Nicotine+ .deb version !"
date: 2006-09-09
forum: Desktop Environments
---

### Post by junglistmaster on 2006-09-09
hello people, i don't suppose anyone can send me in the right direction for the .deb version of nicotine+ 
i just cant install it from a tar!! thanks ahead.

---

### Post by max.diems on 2006-09-09
1. What is Nicotine+
2. Whay can't you compile it?

---

### Post by junglistmaster on 2006-09-09
hi,nicotine+ is apparently the best soulseek client for linux, i dont have the knowledge to compile/install .tar
it is supposed to be avaiable in an easy '1 click' debian install.

[http://ubuntuforums.org/showthread.php?t=196835&highlight=soulseek](http://ubuntuforums.org/showthread.php?t=196835&highlight=soulseek)

---

### Post by max.diems on 2006-09-09
Compiling isn't hard, and sometimes has to be done (not all software is avalible as a .deb), so you should know how.
[LIST=1]
[*]Download the tar file
[*]Unpack it to anywhere
[*]Open a terminal
[*]Type "cd */the/directory/you/unpacked/to*" (for example if you unpacked it to "nicotine" on your desktop type "cd ~/Desktop/nicotine"- the ~/ is a shortcut to your home directory)
[*]After making sure all dependencies are installed, type "./configure; make; sudo make install"[/LIST]Actually, the tar file probably has better instructions in a text file.
NOTE: Everything typed in the terminal is case-sensitive!

---

### Post by junglistmaster on 2006-09-09
thanks max.diems
i will definately give compiling a go, but for all you lazy/windoze educated people here is the link for the best soulseek client
[http://www.osiris.codedchaos.com/osiris/news.php?item.15.5](http://www.osiris.codedchaos.com/osiris/news.php?item.15.5)

---

### Post by INMCM on 2006-09-09
> **junglistmaster said:**
> hello people, i don't suppose anyone can send me in the right direction for the .deb version of nicotine+ 
i just cant install it from a tar!! thanks ahead.

I have a hard time understanding this obsession with only using the  deb. Did you even read the the source based instructions in the thread you quoted?  Becuase it's a python program, there is NO COMPILING if you just want to run Nicotine+ ( the tray icon requires some compiling). I give the EXACT terminal commands to unpack and run the program. I don't want to sound like a grump, but  please read my entire post in the original thread and try running from source. It's really easy. 

Also, this is Linux: some compiling will EVENTUALLY be required, so don't bother trying so hard to avoid it.

---

### Post by junglistmaster on 2006-09-10
Thanks INMCM
i appreciate your effort to compile etc, i did try but to no avail. i found the .deb and it still didnt work. eventually i found the reason; old files from the existing nicotine folder were confusing the install, soo i deleted them and it works, sort of!
all configured and connected, able to search users but all downloads say 'connot connect'
any ideas please?
and yes i must try and get used to this compiling malarchy...

---

### Post by OscarGortez on 2006-09-10
> **junglistmaster said:**
> Thanks INMCM
i appreciate your effort to compile etc, i did try but to no avail. i found the .deb and it still didnt work. eventually i found the reason; old files from the existing nicotine folder were confusing the install, soo i deleted them and it works, sort of!
all configured and connected, able to search users but all downloads say 'connot connect'
any ideas please?
and yes i must try and get used to this compiling malarchy...

Yeah I've been having that same exact problem too, I tried to look at the errors it gives but they really don't make enough sense to me for me to try anything to fix it... Though I do believe the downloads started saying the couldn't connect before i switched to Nicotine + and maybe that was the reason I switched over... I forget and I've just been too lazy to look into it until now...

---

### Post by OscarGortez on 2006-09-10
Alright so I just asked some guys in the chat about it, they suggested I un-check the box that says i can direct connect.  I did and it all works fine now.  So try that out and it should work wonders for you too haha.

---

### Post by junglistmaster on 2006-09-12
Thanks Oscar! you have made my day hombre. its great to be able to use soulseek from linux.

---

