---
title: "gnome missing?"
date: 2006-10-09
forum: Desktop Environments
---

### Post by 2pacalypse on 2006-10-09
this morning i was using my ubuntu system as usual, without root mode only using openoffice and playing abit of Wesnoth, afterwards i turned off my computer normally and he didnt gave me any errors. However around 3-4 hours later i turned on my computer and Gnome didnt worked. its simply booting up into console mode (tty1) and when i try CTRL+ALT+F7 (normal gnome gui mode) he doesnt respond. any ideas how to fix this little prob, or why did it happend in the first place?

---

### Post by s_p_a_r_k_y on 2006-10-09
you could log in as yourself and take a look at /var/log/Xorg.0.log or whatever that file is, or attempt to start GDM by hand, run
```
sudo /etc/init.d/gdm restart
```

---

### Post by 2pacalypse on 2006-10-09
the GDM restart thing didnt worked. he just went down a line and awaited for input, and the document was very long so i havnt really seen it well, but i did noticed plenty of errors in it, 15atleast. so i guess this means my HDD is messed up and i gotta reinstall ubuntu?

---

### Post by s_p_a_r_k_y on 2006-10-09
could you post the file to us for inspection before you go and re-install

---

### Post by 2pacalypse on 2006-10-09
sorry but no. its an extremely long document of 467 lines and the computer im posting from is my sisters Windows machine.

---

### Post by s_p_a_r_k_y on 2006-10-09
you could use Winscp to download the file to her computer and post it from there, I would never ask you to retype it :) 
You could edit out most of it anyway and post the errors sections

---

### Post by 2pacalypse on 2006-10-09
i dont know what win winscp is so i used Samba+Live CD. i'll attack the results now. i had to cut of the start from the xorg.0 file but either way it was Nvidia driver detail... not really importent all the errors are at the end.

---

### Post by s_p_a_r_k_y on 2006-10-09
Winscp is a windows program which allows you to copy files over the SSH protocol. google for winscp. 

Could you also post /etc/X11/xorg.conf

alternatively, you could run this command and replace your xorg config file

```
 sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by 2pacalypse on 2006-10-09
umm, im pretty sure that the X11 setting are ok and the prob is the Gnome... but just to be on the safe side, after all you know better then me

maybe there is a way to reinstall Gnome or install XFCE/KDE from the console mode? it might solve the problem

---

### Post by 2pacalypse on 2006-10-10
Can some1 please help me out with this?, is it possible to salvage Ubuntu or do i have to reinstall the system?. maybe its possible to install KDE/XFCE or reinstall GNOME. maybe that will help.

---

### Post by nealklomp on 2006-10-12
this is disturbing as this has also happened to me and i can see several recent threads of the same occurence.

what is up i wonder.

My situation is that i never turn off my laptop only suspend or hibernate, yet the other day i had to check the battery for that recall of dell batteries and did a complete shutdown for like the first time in months and whammy bammy bad news Gnome would not boot. Login screen comes up but it returns me to login saying the password is bad.

---

