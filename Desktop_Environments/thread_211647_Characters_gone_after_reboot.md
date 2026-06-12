---
title: "Characters gone after reboot"
date: 2006-07-08
forum: Desktop Environments
---

### Post by ruvil on 2006-07-08
Hello.

Today i rebooted my computer and when i typed (for example in an text editor) I saw that some characters where missing (nordic characters, like á 'a' 'o'. I cant type them correctly now.. but you understand what i mean). The wierd thing is that i CAN see the characters, but not write them, so i dont thing there is anything wrong with the "character encoding" (ISO-8859-1)


How do i get these back? (How do i change keyboardlayout?


//Ruvil

---

### Post by ruvil on 2006-07-08
Well.. now i have tried "dpkg-reconfigure locales" this SHOULD come up with a menu or something where i can choose swedish keyboard layout, but when i run that command it only says:
ruvil@bach:~$ sudo dpkg-reconfigure locales
Password:
Generating locales...
  en_US.UTF-8... up-to-date
  sv_SE.UTF-8... up-to-date
Generation complete.
Current default timezone: 'Europe/Stockholm'.
Local time is now:      lör jul  8 23:53:22 CEST 2006.
Universal Time is now:  lör jul  8 21:53:22 UTC 2006.
Run 'tzconfig' if you wish to change it.
ruvil@bach:~$

---

