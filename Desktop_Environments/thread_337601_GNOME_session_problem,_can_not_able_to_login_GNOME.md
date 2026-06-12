---
title: "GNOME session problem, can not able to login GNOME"
date: 2007-01-13
forum: Desktop Environments
---

### Post by moonhk on 2007-01-13
When I turned off computer without shutdown the Ubuntu. Then below error shown can not able to login GNOME. How to fix ?


Your Session only lasted less than 10 seconds. If you have not logged out yourself. This could mean that there is some installation Problem... Try logging in with one of the failsafe sessions to see if you can fix this problem.

When uninstall GNOME desktop then install again , same problem

with following error.

moonhk@hex:~$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x
"/var/lib/gdm/:0.Xservers" -h "" -l ":0" "moonhk"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied
moonhk@hex:~$ directory containing default files

moonhk@hex:~$ uname -a
Linux hex 2.6.15-27-server #1 SMP Fri Dec 8 18:43:54 UTC 2006 i686 GNU/Linux
moonhk@hex:~$ shadow password suite configuration

---

### Post by floke on 2007-01-13
You could try deleting the following files from your home/[yourname] directory.

.gnome
.gconfd
.gconf

(Off the top of my head I think there are another couple of files you need to remove - basically all the files that start with .gnome and .gconf in that directory - you need to enable View/Show Hidden Files obviously to see them).

This will remove you session settings - so you wil lose your desktop settngs (which seem lost anyway) When you restart gnome after this it should setup new ones from scratch.

I had to do this once to resolve a similar issue.

Hope this helps

---

### Post by hal10000 on 2007-01-13
if Steve.K's recommendatios did not help, then remove all your /tmp stuff (But NOT with sudo):
[COLOR="Red"]rm -r /tmp/*[/COLOR]
and log in again

---

### Post by moonhk on 2007-01-13
tried. Not ok.

---

### Post by hal10000 on 2007-01-13
Try to log in with failsave. On the (gdm) login srceen down left choose [COLOR="Red"]settings[/COLOR]--->session--->GNOME failsave. (if you installed kde try kde).
Post wether this works or not.

---

### Post by moonhk on 2007-01-13
Try before. Not not. My ubuntu have not install kde.

---

### Post by moonhk on 2007-01-13
I also try to create other new user id to login Gnome. same Error message prompted.

---

### Post by hal10000 on 2007-01-13
I have found a similar problem: [http://www.ubuntuforums.org/archive/index.php/t-177301.html](http://www.ubuntuforums.org/archive/index.php/t-177301.html)

login to a console (<ALT>+<F2> simultaneously), then do
ls -l /tmp
If you get an error message, then your /tmp directory has somehow gone to nirvana and you have to create a new one:
[COLOR="Red"]sudo mkdir /tmp[/COLOR] and [COLOR="Red"]sudo chmod -R /tmp/ 1777[/COLOR]

If your /tmp still exists, then you may need to delete /tmp/.X0-lock: [COLOR="Red"]sudo rm /tmp/.X0-lock[/COLOR]

---

### Post by moonhk on 2007-01-14
Thank a lot. I just reinstall ubuntu and Gnome again. Its take more than 4 hours. 
Now, I am using partimage and SystemrescueCD to build image for backup. All my data have been backup before reinstall. 

moonhk@moonhk:/mnt/disk2$ ls -lt ubuntu*
-rw------- 1 root root 1186402177 2007-01-14 20:40 ubuntu_20070114.gz.000
-rw------- 1 root root 1051643536 2007-01-14 17:12 ubuntu_gnome.partimg.gz.000
-rw------- 1 root root  202370804 2007-01-14 11:24 ubuntu_server.partimg.gz.000
moonhk@moonhk:/mnt/disk2$

---

