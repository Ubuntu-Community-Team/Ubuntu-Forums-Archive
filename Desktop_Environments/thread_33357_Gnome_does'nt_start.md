---
title: "Gnome does'nt start"
date: 2005-05-10
forum: Desktop Environments
---

### Post by Zaphod Beeblebrox on 2005-05-10
Hi all,

first I have to excuse for my poor English.
Normally I'm posting in the German ubuntuusers.de forum, but since a few day the server is down.

Here is my problem:
When I try to login, ubuntu comes with a error-window with the following message:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jmar"
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:4580): WARNING **: Unable to read ICE authority file: /home/jmar/.ICEauthority

There is a problem with the ICE authority file, Ok, but what is to do?
It will be very kindly if you can answer in short and easy sentences.
Thank you very much.

CU
Z.B.

---

### Post by Xian on 2005-05-10
Please read [THIS](http://ubuntuforums.org/showthread.php?t=7346) thread. Post back with any questions.

---

### Post by Zaphod Beeblebrox on 2005-05-13
Thanx.
That it was.
But why did the permission of the .ICE... File changed to root??

I didn't change.

---

### Post by Alexander Kirillov on 2005-05-13
[QUOTE=Zaphod Beeblebrox]Thanx.
That it was.
But why did the permission of the .ICE... File changed to root??

I didn't change.[/QUOTE]
 Probalby because you started some GUI application as root, via sudo. 
It usually happens to me when I start a KDE app as sudo from GNOME, or the other way around. If youonly use GNOME apps in GNOME, this shoudn't happen.

---

### Post by Bernie01 on 2005-05-27
I have just installed 4.10 and I am having this problem too. I get to the login screen on the command line, enter my login and password then I end up at 'username@ubuntu:~ $' where I type 'startx' and nothing happens.

What have I done wrong?

---

