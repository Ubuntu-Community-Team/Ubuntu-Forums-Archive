---
title: "can't access breezy 5.10"
date: 2006-01-31
forum: Desktop Environments
---

### Post by rlittler2001 on 2006-01-31
I just installed "Breezy 5.10" using install cd. New hard drive(120gb)nothing is on my hard drive but breezy, yet I can't get the password to work and can't access anything. The os will not reinstall  nor can I fromatthe drive. will someone pleas help this new newbie get into his pc.

---

### Post by zojas on 2006-01-31
if it boots into ubuntu and you just can't remember your password, it's easy to fix.

when the computer starts to boot, right after the bios screen, you will see a prompt (for only 2 seconds, so be ready!!) which says something like 'hit esc to enter grub menu'. hit escape during that 2 seconds. then you will get a list of boot options. 

pick the first line which says something like 'recovery mode' in it.

that will probably boot into single user mode and give you a shell prompt as root.

to change the password of your user (I'll assume the username is 'fred') type this:

passwd fred

then enter a new password for fred.

after that finishes, just type 'exit' and it will either reboot  or finish booting up normally. then you should be able to login using your new password. :cool:

---

