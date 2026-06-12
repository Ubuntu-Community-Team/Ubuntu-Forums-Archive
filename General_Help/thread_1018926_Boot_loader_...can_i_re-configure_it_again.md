---
title: "Boot loader ...can i re-configure it again??"
date: 2008-12-22
forum: General Help
---

### Post by shooter07 on 2008-12-22
i install Windows XP then linux Ubuntu , after that i format my windows from my machine ,so i can't select linux Ubuntu from Boot loader screen again when restart pc.

this msg. always appear : " There's no operating system on machine ... or something like that " ?? 

any help plz ?? 

i appreciate that , all the best

---

### Post by jay li on 2008-12-22
Format the windows partition, basically destroyed ubuntu grub too. 
Cause when install Ubuntu, the boot grub loader goes to the first MBR (by default), which means - the windows partition. 

To fix the problem here is a thread that explain how to do it. 
[(http://ubuntuforums.org/showthread.php?t=224351)"][COLOR="Blue"]***_How to restore Grub from a live Ubuntu cd_***[/COLOR]]("[http://ubuntuforums.org/showthread.php?t=224351)

---

