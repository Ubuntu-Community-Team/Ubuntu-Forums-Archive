---
title: "Two distores, one home partion"
date: 2008-12-06
forum: General Help
---

### Post by epqr on 2008-12-06
Ok so i have ubuntu 8.04 installed on a 5gb. Then i have a 30gb partion i use as /Home. Now i tried to install another distro and i put it to use the same /Home partion. Of course i did not use the same usernames on the distroes. Now my ubuntu won't boot. i come to the loading screen, but after that is finished the screeb just goes blank. I can write whatever i want, but it doesnt have any effect.. Anything i can do to fix this?

---

### Post by epqr on 2008-12-06
Anyone? Its just like a black screen . I tried to leave it on for an hour and nothing changed

---

### Post by louieb on 2008-12-06
Sounds like when you installed the 2nd distro - you had it format the /home partition, wiping out all the data on it. Use your 2nd distro and look in /home and see if there is a folder with the Ubuntu user name. If there is then theres a good chance Ubuntu can be fixed .

If not get a [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and run a program called photorec and see what it can recover..

---

### Post by epqr on 2008-12-06
Ive check the old user is still there along with all my documents from the old distro

Edit; i have also tried to boot in recovery mode. Doesnt help

---

### Post by louieb on 2008-12-06
Good.  Now I guess the new distro set its own GRUB to show at boot? right?
and you have a Ubuntu entry. Compare the Ubuntu entry in the 2nd disto with the one in Ubuntu. For Ubuntu the file you want is /b**oot/grub/menu.lst**.
What is the 2nd distro? Probably the grub configuration file has the same name. But it might be called /boot/grub/grub.conf.

---

### Post by epqr on 2008-12-06
I got it working now. i changed the line 
"/boot/vmlinuz-2.6.24-16-generic root=/dev/sda9 ro quiet splash " 
 to "/boot/vmlinuz-2.6.24-16-generic root=/dev/sda8 ro quiet splash"

Thanks for the help :)

---

