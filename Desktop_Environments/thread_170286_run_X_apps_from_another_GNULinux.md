---
title: "run X apps from another GNU/Linux"
date: 2006-05-04
forum: Desktop Environments
---

### Post by insulae on 2006-05-04
(sorry for my english :) )

i have installed in my machine 2 ubuntus:

/dev/hda1: Xubuntu Dapper
/dev/hda2: kubuntu breezy

i don't like use QT and GTK+ togethers, so i have xubuntu and kubuntu, i like very much gnome/xfce, but gnome/xfce don't have a good php/html editor like quanta (is great the quanta html completation). 

so i want to run in my xubuntu the quanta what i have in kubuntu (i dont want install quanta in xubuntu, just run), i tried to do that with a simple chroot but i have the next error:  cannot connect to X server. 
i try a gentoo howto, but with the gentoo howto i can start another X with all KDE, hehehe, but i don't want this.

thanks =).

---

### Post by Harleen on 2006-05-04
You can allow anyone to access your X-Server with this command
```
xhost +
```
After that, your chroot method may work. I haven't tried it myself, of course...

---

### Post by Biker on 2006-05-04
I assume openssh is installed on both machines. So run from cli on the xubuntu server "ssh -X hostname-kubuntu". You are now logged in on the kubuntu machine and you can start quanta from the cli.

---

### Post by pelago on 2006-05-04
I think he only has one machine, with two partitions with different distributions of Ubuntu.

---

### Post by insulae on 2006-05-04
Biker, pelago has right, i have one machine, so don't work for my ssh, but... the > xhost + from Harleen WORKS GREAT!!!, i can run my quanta/kubuntu/hda2 application in my xubuntu/hda1 GNU/Linux :P.
is to easy hehehe, i try many crazys howto, and only need the "xhost +" =).

thanks to: Harleen, Biker and pelago, i try this for 2 week with not result. And a one post in [www.ubuntuforums.org](www.ubuntuforums.org) you give me the answer in 20 minutes =).

---

### Post by louis_nichols on 2006-05-04
Interesting thread. So let me see if I got this right, cuz I might use it sometime:

I install, say, Xubuntu on /dev/hda1 and Kubuntu on /dev/hda2 . Then I start Kubuntu, log in, open a terminal and do

```

$xhost +
$chroot <mount point of /dev/hda1>
$<gnome app executable>

```

and it works?

---

### Post by insulae on 2006-05-04
yes louis_nichols, but... i try this in my work, with the next configuration:

in /dev/hda2 ubuntu (gnome)

so i dont have in the work 2 linux, so... i run with a SLAX live CD, then i run 
```

$xhost +
$chroot /mnt/hda2 (slax use automount)
$gnomebaker 

```

and work wonderfull!! 
but now in my home i try with 2 ubuntus (my first example)
[I] /dev/hda1: Xubuntu Dapper
 /dev/hda2: kubuntu breezy
[/I]
but don't work hehe, so i now searching info to see how work the comand xhost, and how is set in ubuntu.

conclution:  from slax to ubuntu chroot is fine. from ubuntu to ubuntu chroot don't work for me.

---

### Post by insulae on 2006-05-05
I RESOLVED MY PROBLEM!!!

my problem was GDM, you most do in ubuntu this:
run gdmsetup
```
 sudo gdmsetup
```
go to the security section and uncheck the **option "Deny TCP connections to Xserver"**

now you most do
```

sudo mount /dev/hda2 /mnt/hda2 (to mount your another linux)
xhost + (to allow "guest connections")
sudo chroot /mnt/hda3 (to go to another linux)
quanta -display InZu:0 (to run the application) **

```
** InZu is the name of my machine, you can use localhost or 127.0.0.1 to, or you can use the command 
```
 export DISPLAY=localhost:0
```
with this you only need run the application:
```

quanta

```

meaby for security reason you most change the command:
```
 xhost +
```
for:
```
xhost +localhost
```
with this you only give permition for the localhost machine.

---

