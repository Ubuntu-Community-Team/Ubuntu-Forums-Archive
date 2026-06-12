---
title: "script in init.d not running at startup"
date: 2005-12-29
forum: Desktop Environments
---

### Post by marks_linux on 2005-12-29
I have the following script in /etc/init.d

> /home/markw/fah1.log
touch /home/markw/fah1.log
> /home/markw/fah2.log
touch /home/markw/fah2.log
cd /home/markw/fold1/
/home/markw/fold1/FAH502-Linux.exe -local -forceasm > /home/markw/fah1.log &
cd /home/markw/fold2/
/home/markw/fold2/FAH502-Linux.exe -local -forceasm > /home/markw/fah2.log &

Essentially tostart up two instances of folding@home.
The script runs fin is i run it by hand. but does not run when the machine reboots?
permissions are rwxr-xr-x on the script.

Anyone help?

---

### Post by pharcyde on 2005-12-29
You have to edit the run level of the scripts stored in /etc/init.d.  This can be accomplished by installing/using a simple command run level editor.

try:
[B]
cp <yourscript> /etc/init.d/.
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
[/B]

After sysv-rc-conf is running change the run level of the script to have it execute during boot.

---

### Post by robotgeek on 2005-12-29
You can simply put your script in /etc/init.d/ and run "sudo update-rc.d <script> defaults

---

### Post by dcstar on 2005-12-29
[QUOTE=marks_linux]I have the following script in /etc/init.d

> /home/markw/fah1.log
touch /home/markw/fah1.log
> /home/markw/fah2.log
touch /home/markw/fah2.log
cd /home/markw/fold1/
/home/markw/fold1/FAH502-Linux.exe -local -forceasm > /home/markw/fah1.log &
cd /home/markw/fold2/
/home/markw/fold2/FAH502-Linux.exe -local -forceasm > /home/markw/fah2.log &

Essentially tostart up two instances of folding@home.
The script runs fin is i run it by hand. but does not run when the machine reboots?
permissions are rwxr-xr-x on the script.

Anyone help?[/QUOTE]

Notice how all the other scripts have a line like "#!/bin/sh" as their first line?.....

---

### Post by marks_linux on 2005-12-29
thanks for the quick replies. Am going to work through them. Got sysv-rc-conf installed but its not showing my script. going through the man pages now!
M

---

### Post by marks_linux on 2005-12-29
thanks guys.

Everything running after doing the: sudo update-rc.d <script> defaults

---

### Post by hw-tph on 2005-12-29
A good hint would be reading /etc/init.d/README too.... ;)


H&#229;kan

---

