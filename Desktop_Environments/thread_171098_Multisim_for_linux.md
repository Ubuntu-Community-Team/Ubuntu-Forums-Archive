---
title: "Multisim for linux?"
date: 2006-05-05
forum: Desktop Environments
---

### Post by DarkManX4lf on 2006-05-05
Has anyone got Multisim to work in linux using wine or something? or does anyone know a good program that is equivalent to multisim for linux?

---

### Post by trent dillman on 2006-05-05
...

---

### Post by DarkManX4lf on 2006-05-06
ok i tried  to run the multisim install on wine, but it didnt work, it gave me some error...so i managed to get crossover office, and i managed to get in rpm and debian format, how do i install it?

---

### Post by DarkManX4lf on 2006-05-06
ok well i got crossover office installed and i tried to install multisim with it, and man it just woulndt work...has anyone managed to install multisim on linux? its the ONLY thing holding me back from using linux....anyone?

---

### Post by Omnios on 2006-05-06
Found this on Google.
[http://www2.linuxjournal.com/article/3008]("http://www2.linuxjournal.com/article/3008")
[http://www.gnu.org/software/electric/electric.html]("http://www.gnu.org/software/electric/electric.html")
[http://bach.ece.jhu.edu/~tim/programs/xcircuit/]("http://bach.ece.jhu.edu/~tim/programs/xcircuit/")

---

### Post by DarkManX4lf on 2006-05-06
yeah those are pretty much good programs i guess, but the problem is most of the people that i work with use multisim so if i have created a project using one of those programs i wouldnt be able to share it with them....there must be a way to get  multisim to work in linux....

---

### Post by trent dillman on 2006-05-07
...

---

### Post by DarkManX4lf on 2006-05-07
[QUOTE=trent dillman]You could install Multisim on a Windows Virtual Machine using VMWare or Qemu...[/QUOTE]


how would i do that tho?

---

### Post by dmizer on 2006-05-07
[QUOTE=DarkManX4lf]how would i do that tho?[/QUOTE]
try here ... [http://www.ubuntuforums.org/showthread.php?t=154265&highlight=qemu](http://www.ubuntuforums.org/showthread.php?t=154265&highlight=qemu)

---

### Post by DarkManX4lf on 2006-05-07
[QUOTE=dmizer]try here ... [http://www.ubuntuforums.org/showthread.php?t=154265&highlight=qemu](http://www.ubuntuforums.org/showthread.php?t=154265&highlight=qemu)[/QUOTE]


thanks that worked, now i have one more question, say i wanted to transfer a file from my linux destop to the emulated windows desktop how would i do that?

---

### Post by dmizer on 2006-05-09
set up samba, and  you can transfer files.  i have not been able to trasfer from the emulated windows to linux, but from linux to windows was no problem once i got samba set up correctly.

---

### Post by DarkManX4lf on 2006-05-09
[QUOTE=dmizer]set up samba, and  you can transfer files.  i have not been able to trasfer from the emulated windows to linux, but from linux to windows was no problem once i got samba set up correctly.[/QUOTE]

yeah i have samba setup and i can share files from my home network....

how about getting a usb drive to work in the emulated windows? i cant seem to get that to work......

---

### Post by DarkManX4lf on 2006-05-10
ok this is really annoying,  i managed to get winxp installed in qemu, and the first time i did it i could install multisim with no problems and multisim ran with no problems, then for some reason windows wouldnt boot up anymore (in qemu) so i deleted that fake partition and reinstalled it and now everytime i try to install multisim it wont work, it wont install at all.....can anyone help ?

---

### Post by dmizer on 2006-05-16
if you have a copy of windows 2000 it might work better.  i believe i read somewhere that qemu has a bit of difficulty with windows xp.

i do, however, freely resign my comment if someone more knowledgeable than myself comes along.

---

