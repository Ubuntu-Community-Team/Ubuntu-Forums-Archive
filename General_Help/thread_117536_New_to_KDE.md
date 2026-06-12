---
title: "New to KDE"
date: 2006-01-15
forum: General Help
---

### Post by prophet of the pimps on 2006-01-15
ok last week i installed ubuntu 5.04. i liked it so i downloaded the latest version but this time i decided to use kubuntu 5.10 just ot give the kde a try.

how does one edit the boot menu in KDE.

i know the cmd in ubuntu

sudo gedit /boot/grub/menu.lst

but whats the equivalent of this command in KDE.

Also another question is where is the automatic log in located in KDE?

---

### Post by PsychoTrauma on 2006-01-15
```
sudo kwrite /boot/grub/menu.lst
```

That should work for you. If you dont mind using command line you could also do:

```
sudo nano /boot/grub/menu.lst
```

---

### Post by GeneralZod on 2006-01-15
[QUOTE=prophet of the pimps]
Also another question is where is the automatic log in located in KDE?[/QUOTE]

Hi there,

I'm not quite sure what you mean by this; can you explain? The standard logs are of course still in the same place (/var/log/).  Try K-Menu->System->KSystemLog for a GUI.

[http://etotheipiplusone.com/ksystemlog.png](http://etotheipiplusone.com/ksystemlog.png)

---

### Post by prophet of the pimps on 2006-01-15
figured it out on my own.

the boot file i edited using the gui under the kdesu konqueror mod.

Also the auto login is hidden inside the user setting.

seriously the kdesu command is really helpful for us windows user.

also the apt-get install ubuntu-desktop isnt working. i wanna install gnome also.

And final request. my isp reqires me to use a client to log on to the net.
its in tar format. how do i install it?

---

### Post by prophet of the pimps on 2006-01-15
ok i got everything working just as i want. got the drives to mount also but i have a small problem.

The mounted drives can only be accessable by the root user (using the KDESSU konqueror command). how can i allow the other user to access it also. Also how do i make it so that they get mounted at every boot up.

---

### Post by nrwilk on 2006-01-15
This is an excellent place to look first for help with stuff.
It's solved multiple problems for me.

[http://ubuntuguide.org/](http://ubuntuguide.org/)

specifically, this section of it worked perfectly for me to do exactly what you're doing:

for mounting NTFS partitions:
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

for mounting FAT partitions:
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

I hope these help!

---

### Post by artnay on 2006-01-15
[QUOTE=PsychoTrauma]```
sudo kwrite /boot/grub/menu.lst
```

That should work for you. If you dont mind using command line you could also do:

```
sudo nano /boot/grub/menu.lst
```[/QUOTE]

No, it's "kdesu kwrite /boot/grub/menu.lst". For launching GUI applications, use gksudo or kdesu, depending on your DE! And you probably would like to start nano with "nano -w" so it wouldn't mess your lines.

---

### Post by prophet of the pimps on 2006-01-16
from now on i am doing all my editing using the GUI with the KDESU command. it makes life a hell of a lot easier.

thanks everyone for the help. :D

---

