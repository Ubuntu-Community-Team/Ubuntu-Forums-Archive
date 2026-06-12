---
title: "installing Savage2Install-1.4.7-x86_64.bin on jaunty"
date: 2009-04-29
forum: Gaming &amp; Leisure
---

### Post by karimruan on 2009-04-29
okay, I have jaunty 64 bit and downloaded Savage 2 64 bit. I tried this:

mat@ubuntu:~$ cd /home
mat@ubuntu:/home$ sudo sh ~/Savage2Install-1.4.7-x86_64.bin
[sudo] password for mat: 

and got this:

sh: Can't open /home/mat/Savage2Install-1.4.7-x86_64.bin
mat@ubuntu:/home$ 

anyone know how i can install this game?

---

### Post by maheshjr2000 on 2009-04-29
Ya try sudo ./Savage2Install-1.4.7-x86_64.bin

If not you might want to check permissions.

---

### Post by Vadi on 2009-04-29
Open a terminal, drag the .bin file into it, and press enter. Try that.

---

### Post by Perfect Storm on 2009-04-30
> **karimruan said:**
> okay, I have jaunty 64 bit and downloaded Savage 2 64 bit. I tried this:

mat@ubuntu:~$ cd /home
mat@ubuntu:/home$ sudo sh ~/Savage2Install-1.4.7-x86_64.bin
[sudo] password for mat: 

and got this:

sh: Can't open /home/mat/Savage2Install-1.4.7-x86_64.bin
mat@ubuntu:/home$ 

anyone know how i can install this game?

Guide; [http://gaming.gwos.org/doku.php/guides:64bit:savage_2](http://gaming.gwos.org/doku.php/guides:64bit:savage_2)

---

### Post by karimruan on 2009-10-07
Sorry it took so long to reply. I switched to Jaunty 32 bit, and am going to try savage 2 32bit now. I will let you know how it goes!

---

### Post by DrMelon on 2009-10-07
Don't use sh to open it.
Just type > ./Savage2Install-1.4.7-x86_64.bin when you're in the directory to open it. It worked for me!
If that still fails to work, use > sudo ./Savage2Install-1.4.7-x86_64.bin

If it still doesn't work, make sure the permissions are set to allow it to be executed.

---

