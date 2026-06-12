---
title: "First boot after fresh install- circular file!"
date: 2008-07-25
forum: Fedora/RedHat and derivatives
---

### Post by kvk on 2008-07-25
I just did a fresh install of F9 on an old Gateway laptop, using CD ISOs 1-4 from the Fedora download page. Installation went fine with no issues. First boot after install goes directly to a log-in dialogue box, instead of Set-Up, License, User Creation, and such. The only user that exists is root, and if I log on as root, the sytem tells me that's a bad idea and returns to the prompt. Circular file!! :(

Any ideas on this one? :)

Thank you!

---

### Post by shawnansasio on 2008-07-28
Well if you are a little good with linux follow these instructions:
Otherwise download Ubuntu Linux.

Step 1. hit Ctrl + alt + F3 (or anything below F5)

Step 2. You will get a black non-gui login window , 
Login as root (it will not stop you)

Step 3. Now if you get a shell type: useradd myusername -d /home/myusername
Where "myusername" is the username of your choice And /home/myusename is your home dir.

Step 4.now type: passwd myusername
Here is where you setup your password

Step 5. Now reboot and try loging in as the new user!!!

Hope This helps!

_______________________________________

I am a 9 year old linux MASTER!!!!
Really.

---

### Post by kvk on 2008-07-29
Excellent! I'll try that-thanks so much!

I already run Ubuntu on another machine- this is my "toy" laptop I got from State surplus to play with, distro hop, and find the perfect set of OS, editors, IDEs and such before modifying one of my primary machines. :)

---

### Post by shawnansasio on 2008-07-30
No problem.

GOOD LUCK!!! :)

_______________________
I am a 9 year old linux
MASTER!!

---

### Post by kvk on 2008-07-31
Hmmm...everything goes great until setting the password for the new user account. The new user shows in the log-in prompt after rebooting, but whenever I try to set or reset the password, the return after typing and confirming the password is:

User not known to the underlying authentication module.

What now? :-)

---

### Post by shawnansasio on 2008-07-31
Is it the passwd command that is not working or the login window that is not letting you log on.


__________________________________

I am a 9 year old linux MASTER!!!

---

### Post by kvk on 2008-07-31
It's the password command under root log-in in the terminal. It will allow me to createthe user account, but not define a password for it.

---

