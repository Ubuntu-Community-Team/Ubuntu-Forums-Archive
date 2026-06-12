---
title: "start up programs"
date: 2006-04-22
forum: Desktop Environments
---

### Post by amunimanghi on 2006-04-22
hi does anyone know how to make firestarter automatically start up on boot up. also, how can i change the permissions for firestarter. i dont why it has a password anyway. :p

---

### Post by Ramses de Norre on 2006-04-22
sudo gedit /etc/sudoers
insert a line ```
username     /usr/sbin/firestarter = NOPASSWD: ALL

```
Then System > preferences > sessions > startup programs tab > add 
Command is firestarter --start-hidden, order=50

---

### Post by amunimanghi on 2006-04-22
thank you very much. it worked.

---

### Post by Jawbreaker4Fs on 2006-04-22
AHH! I edited the sudoers file like you said to do this... and I must have done it wrong because every time I try to use a sudo command, I get the following error:

```

>>> sudoers file: syntax error, line 21 <<<
sudo: parse error in /etc/sudoers near line 21

```

HELP! I made a backup of the file, but I can't restore the sudoers file without sudo access! How can I fix this?!?!?!

---

### Post by Jawbreaker4Fs on 2006-04-22
Ok.. fixed it by rebooting in recovery mode and changing the file back. Whew!

---

### Post by amunimanghi on 2006-04-22
what did you do to fix it? it happened to me to!  > AHH!

---

### Post by Sutekh on 2006-04-23
You should really edit the /etc/sudoers file with
```
sudo visudo
```
This edits a temporary version and check for syntax errors before writing to /etc/sudoers.

See```
man visudo
```

To get the backup restored (assuming you made one in the first place) you should boot to recovery mode from GRUB.  You should have a menu entry 
```
title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
```
Once in recovery mode copy the backup over the corrupted /etc/sudoers

---

### Post by amunimanghi on 2006-04-23
k i fixed it. thanks

---

