---
title: "Xsession problem"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Coyne on 2005-12-15
Hey, i'm having a problem again.
When I log on,I get a notice that I will be logged of within 10 seconds.
I get following error:
x-session-manager: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory.

Can anyone help me with this. Please consider that i'm new in the whole linux thing.

---

### Post by dcstar on 2005-12-15
[QUOTE=Coyne]Hey, i'm having a problem again.
When I log on,I get a notice that I will be logged of within 10 seconds.
I get following error:
x-session-manager: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory.

Can anyone help me with this. Please consider that i'm new in the whole linux thing.[/QUOTE]
After you are kicked out, press (at the same time) <CTRL><ALT><F1>, then at the "login:" prompt, enter your username (and Enter) and then your password, you should then be logged in at a terminal session.

Then type "su" (followed by Enter) and enter your root password (which may be the same as you user password) when prompted, you will then be logged in as root user.

Type in "cd /usr/lib" (and then Enter....) and then "ls -al libasound*"

You should see something like the following:
[I]
lrwxrwxrwx  1 root root     18 2005-10-29 13:23 libasound.so.2 -> libasound.so.2.0.0
-rw-r--r--  1 root root 729568 2005-06-09 19:22 libasound.so.2.0.0[/I]

If you don't see this, then type:

apt-get install libasound2

---

### Post by porter on 2006-01-08
ok, i have the same problem. 

doing the sudo apy-get thing i get "libasounds is already the newest version. 0 upgraded, 0 installed, 0 to remove and 13 not upgraded"

doing the ls -al libasound* gets "no such file or directory"

any other ideas?

thanks.

---

### Post by dcstar on 2006-01-08
[QUOTE=porter]ok, i have the same problem. 

doing the sudo apy-get thing i get "libasounds is already the newest version. 0 upgraded, 0 installed, 0 to remove and 13 not upgraded"

doing the ls -al libasound* gets "no such file or directory"

any other ideas?

thanks.[/QUOTE]
Search your system for that file spec using the "Search for files" function.

---

### Post by porter on 2006-01-08
searching would be great if i could get into a gui.....

---

### Post by greasepain37 on 2006-01-11
[QUOTE=Coyne]Please consider that i'm new in the whole linux thing.[/QUOTE]

more newbie then thou

i seem to be having the same problem. i attempt the above directions but when i enter "cd /usr/lib" (and then Enter....) and then "ls -al libasound*" i get no such directory.

---

