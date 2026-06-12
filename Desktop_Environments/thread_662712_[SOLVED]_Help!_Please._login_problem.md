---
title: "[SOLVED] Help! Please. login problem"
date: 2008-01-09
forum: Desktop Environments
---

### Post by cobalt69 on 2008-01-09
Ok, so im not exactly new to linux but im not a lvl 70 linux user, anyway i seem to have messed up my login i changed to login dir from /home/oem to /home/cobalt and it tells me that it cant login due to the dir not existing or something and i coud try in failsafe so the only failsafe i have working is terminal so can anyone help me fix my mistake :) please :(

---

### Post by taurus on 2008-01-09
Boot into recovery mode from GRUB menu and modify your /etc/passwd and make sure you change the $HOME directory to /home/cobalt.

```
nano -Bw /etc/passwd
```
Save it with <Ctrl>o and exit with <Ctrl>X.  Reboot with

```
shutdown -r now
```

p.s.  Just so you know.  You installed the oem version and if you look at the screen during the installing process, it tells you that you can create a user with root privilege by running a command from a terminal after you log in the first time with oem account.  Changing your login name from oem to cobalt is not the way to go.

```
sudo oem-prepare-config
```

---

### Post by cobalt69 on 2008-01-09
thanks ill try that i should have known that wasnt the way to change it lol i have used linux before but i mostly used windows so i guess im still in conversion and understanding the way linux thinks its not as stupid as windows i guess you could say but not as user friendly i guess thats what i like about it (well besides the awesome things you can do with it and the overall better performance)

---

### Post by cobalt69 on 2008-01-10
ok i ended up just reinstalling and not doing it as an oem install

---

