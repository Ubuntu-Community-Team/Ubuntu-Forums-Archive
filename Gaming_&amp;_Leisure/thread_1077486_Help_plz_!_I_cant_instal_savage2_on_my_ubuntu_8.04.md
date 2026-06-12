---
title: "Help plz ! I cant instal savage2 on my ubuntu 8.04"
date: 2009-02-22
forum: Gaming &amp; Leisure
---

### Post by nicolay on 2009-02-22
hi , i have ubuntu for like 1 month now , and i try to instal savage2 but its .bin , and my ubuntu wont instal the file ... anny 1 can help me ? 
i downloaded 32 bit and 64 bit becouse i dont know wat i have ...

grtz nicolay:(

---

### Post by Perfect Storm on 2009-02-22
Here's a guide (64bit); [http://gaming.gwos.org/doku.php/guides:64bit:savage_2](http://gaming.gwos.org/doku.php/guides:64bit:savage_2)
If it complains about wrong structure, then you sure have 32-bit Ubuntu. Then just make the changes if you follow the guide to 32-bit (name changes etc.)

---

### Post by crazyfuturamanoob on 2009-02-22
Open a terminal, type in "uname -m". If it gives you x86_64 then you got 64bit Ubuntu. Otherwise 32bit.

---

### Post by nicolay on 2009-02-22
> **Artificial Intelligence said:**
> Here's a guide (64bit); [http://gaming.gwos.org/doku.php/guides:64bit:savage_2](http://gaming.gwos.org/doku.php/guides:64bit:savage_2)
If it complains about wrong structure, then you sure have 32-bit Ubuntu. Then just make the changes if you follow the guide to 32-bit (name changes etc.)

if i do the steps this is what i get ..  
nicolay@nicolay-desktop:~$ mkdir ~/.Games
mkdir: cannot create directory `/home/nicolay/.Games': File exists
nicolay@nicolay-desktop:~$ cd ~/Desktop
bash: cd: /home/nicolay/Desktop: No such file or directory
nicolay@nicolay-desktop:~$ 


:(

---

### Post by Vadi on 2009-02-22
That's a funny one, your desktop folder is gone.

use "mkdir ~/Desktop" to make it

---

### Post by nicolay on 2009-02-22
> **crazyfuturamanoob said:**
> Open a terminal, type in "uname -m". If it gives you x86_64 then you got 64bit Ubuntu. Otherwise 32bit.

ok ty now i know i have 32 bit but still cant instal -_-'  
:(

---

### Post by nicolay on 2009-02-22
> **Vadi said:**
> That's a funny one, your desktop folder is gone.

use "mkdir ~/Desktop" to make it


ty now i have the folder :) 
but still cant instal  

: nicolay@nicolay-desktop:~$ mkdir ~/Desktop
nicolay@nicolay-desktop:~$ mkdir ~/.Games
mkdir: cannot create directory `/home/nicolay/.Games': File exists
nicolay@nicolay-desktop:~$ cd ~/Desktop
nicolay@nicolay-desktop:~/Desktop$ chmod +x Savage2Install-1.5.0-i686.bin
chmod: cannot access `Savage2Install-1.5.0-i686.bin': No such file or directory
nicolay@nicolay-desktop:~/Desktop$ Savage2Install-1.5.0-i686.bin
bash: Savage2Install-1.5.0-i686.bin: command not found
nicolay@nicolay-desktop:~/Desktop$ chmod +x Savage2Install-1.3.99-1.5.0-i686.bin
chmod: cannot access `Savage2Install-1.3.99-1.5.0-i686.bin': No such file or directory
nicolay@nicolay-desktop:~/Desktop$ '/home/nicolay/Bureaublad/Savage2Install-1.5.0-i686.bin' 
bash: /home/nicolay/Bureaublad/Savage2Install-1.5.0-i686.bin: Permission denied
nicolay@nicolay-desktop:~/Desktop$

---

### Post by Vadi on 2009-02-22
Did you put the file in your desktop?

Anyway, here are some easier, graphical instructions...


Right-click on *Savage2Install-1.5.0-i686.bin*, click on *Properties*, *Permissions* tab, and enable "allow executing file".

Then drag the file into the terminal window and press enter.

---

### Post by nicolay on 2009-02-22
> **Vadi said:**
> Did you put the file in your desktop?

Anyway, here are some easier, graphical instructions...


Right-click on *Savage2Install-1.5.0-i686.bin*, click on *Properties*, *Permissions* tab, and enable "allow executing file".

Then drag the file into the terminal window and press enter.

thank you very much !
your the best ;)

---

### Post by Vadi on 2009-02-22
Enjoy the game!

---

### Post by nicolay on 2009-02-22
> **Vadi said:**
> Enjoy the game!

omg problem again :s 

if i play the game my screen flashes black :(
damm i hate linux , with windows u never have problems with games :s

---

### Post by Vadi on 2009-02-22
you have other problems with windows though ;)

what video card do you have?

---

