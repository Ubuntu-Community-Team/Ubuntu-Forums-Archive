---
title: "changing root hdd to another (larger) hdd???"
date: 2006-09-04
forum: Desktop Environments
---

### Post by master5o1 on 2006-09-04
I just got a free 10GB hdd and want to replace my current 4gb root hdd with this (yes, awefully small!!)...

heres my little layout:

4gb = /root (3.x gb); swap (250mb)
20gb = /home
10gb = (nothing) ...want to make it root

and with the 4gb HDD i want to make it my /var (for apache).

So if anyone is kind enough to help me switch my current ROOT to this new 10gb, and my /VAR to the old 4gb, then it would be much appreciated :)

---

### Post by dbasis on 2006-09-04
well i got less beeans and I´m not completely sure, but it should work out if u mount the new hd and then type in yur terminal
"sudo cp -a /dev/hda1 /mnt/<newdisk>"
then turn down your machine, switch the harddisk and try to reboot

in an second step if that above worked out u copy the "/var"  directory(?) to your 4gb disk like above and change the settings in "/etc/fstab" and make the mount pont of the thir hdd to "/var"

well as i sayed I´m not 100% sure, but i think it should work out

let me please know

---

