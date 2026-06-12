---
title: "What is the difference between root and me_"
date: 2005-06-03
forum: Desktop Environments
---

### Post by xo310 on 2005-06-03
Hi.
I am trying to modify xfree86 but it says that this file is read only and when i try to change that it says that i am not the owner and that the owner is the root.
How do i become the root? or more specifically how do i edit permissions of that file?
thanks

---

### Post by lorap on 2005-06-03
hi friend!
to get the root's rights you need just write "sudo" before any command like this:

sudo gedit yourfilename

have a nice day.
pavel

---

### Post by codejunkie on 2005-06-03
first don't change premissons for that file if you don't know what your doing trust me i've been there done that. the root user is there so if something gets broken in a user account it doesn't take the whole system with it basicly the administrator account. but you need premission to access system configuration utilities and system files so use sudo so if you wan't to edit xfree86 open a terminal and type sudo gedit /etc/X11/xfree86.conf if this is the file you want to edit, it will ask for a password enter your user password.

---

### Post by lorap on 2005-06-03
sorry,
to change permissions you've to do the next:

4 - read
2 - write
1 - execute

6 - (4+2) read/write

7 - (4+2+1) read/write/execute

sudo chmod 755 /home/yourusername/filename

have a nice day!
pavel

---

### Post by xo310 on 2005-06-03
thak you very much all

---

### Post by Joeb on 2005-06-03
Actually, the reason you are having permission problems with xfree86 is because you AREN'T root.  If you place sudo in front of your edit command as others have suggested (ie.  sudo vi myfilename), you shouldn't have to change the permissions, at least not for most configuration files.

Joeb

---

