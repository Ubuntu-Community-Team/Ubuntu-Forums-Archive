---
title: "HELP...HELp...HElp...Help...help"
date: 2006-06-29
forum: Desktop Environments
---

### Post by spincricket on 2006-06-29
Hi guys, I need some help. You see I installed Xubunu 6.06 . 

I hate it, I hate xfce4, it just feels limited...I just cant take it.

I want to use kde instead. Now, im on a 256k dsl connection (all thats available) so i dont want to have to download the kubuntu iso.

Is there a way to remove the xubunu-desktop from this xubuntu install, and reinstall KDE on top of that?

I could try the server install and install the kubuntu-desktop, but it has a bunch of dependency issues.

#-o 

Can anyone help me?

---

### Post by ahaslam on 2006-06-29
[QUOTE=spincricket]Hi guys, I need some help. You see I installed Xubunu 6.06 . 

I hate it, I hate xfce4, it just feels limited...I just cant take it.

I want to use kde instead. Now, im on a 256k dsl connection (all thats available) so i dont want to have to download the kubuntu iso.

Is there a way to remove the xubunu-desktop from this xubuntu install, and reinstall KDE on top of that?

I could try the server install and install the kubuntu-desktop, but it has a bunch of dependency issues.

#-o 

Can anyone help me?[/QUOTE]

Simply open up synaptic, search for and install kubuntu-desktop.
You'll be able to choose your session at the login screen. You should also be able to remove xubuntu-desktop, if you want KDE only.

I hope that helps,

Tony.

---

### Post by spincricket on 2006-06-29
thanks. Going to try that right now.!

---

### Post by Jasper Houtman on 2006-06-29
boot up with command promt only.
type:

sudo apt-get remove xubuntu-desktop
sudo apt-get install kubuntu-desktop

---

### Post by angkor on 2006-06-29
[QUOTE=Jasper Houtman]
sudo apt-get remove xubuntu-desktop
[/QUOTE]

This command will not remove xfce4 from your system. It will simply remove the xubuntu-desktop metapackage.

---

### Post by gingermark on 2006-06-29
[QUOTE=Jasper Houtman]boot up with command promt only.
type:
sudo apt-get remove xubuntu-desktop
[/QUOTE]
This does nothing but remove the xubuntu meta-package.
[QUOTE=Jasper Houtman]
sudo apt-get install kubuntu-desktop[/QUOTE]
use aptitude instead. This will mean if you decide you don't like Kubuntu you can easily remove is later. So:
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by Jasper Houtman on 2006-06-29
Misasumption, How do you do that then?

Edit: thanks!

---

### Post by spincricket on 2006-06-29
I tried it guys and it says this:

```
fito@mylinux:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "kubuntu-desktop"
The following packages have been kept back:
  acpi-support binutils-static desktop-file-utils firefox gdm gnupg
  gtk2-engines-clearlooks gtk2-engines-industrial gtk2-engines-mist
  gtk2-engines-smooth language-pack-en libfreetype6 libglib2.0-0
  libglib2.0-data libgnomeprint2.2-0 libgnomeprint2.2-data libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libnspr4 libnss3 libpango1.0-0
  libpango1.0-common libtiff4 libvte-common libvte4 libxine-main1
  linux-image-386 mozilla-thunderbird python-vte wpasupplicant xfce4-mixer
  xfce4-mixer-alsa xfdesktop4
0 packages upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by angkor on 2006-06-29
See

[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

for removing xubuntu alltogether

---

### Post by Jasper Houtman on 2006-06-29
[QUOTE=angkor]See

[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

for removing xubuntu alltogether[/QUOTE]

Thank god for copy and paste :P
Thanks for the info!

---

### Post by gingermark on 2006-06-29
[QUOTE=spincricket]I tried it guys and it says this:

```
fito@mylinux:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "kubuntu-desktop"
The following packages have been kept back:
  acpi-support binutils-static desktop-file-utils firefox gdm gnupg
  gtk2-engines-clearlooks gtk2-engines-industrial gtk2-engines-mist
  gtk2-engines-smooth language-pack-en libfreetype6 libglib2.0-0
  libglib2.0-data libgnomeprint2.2-0 libgnomeprint2.2-data libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libnspr4 libnss3 libpango1.0-0
  libpango1.0-common libtiff4 libvte-common libvte4 libxine-main1
  linux-image-386 mozilla-thunderbird python-vte wpasupplicant xfce4-mixer
  xfce4-mixer-alsa xfdesktop4
0 packages upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```[/QUOTE]
did you do a 'sudo aptitude update' first? If so, can you post the contents of your sources.list list file (located in /etc/apt) please.

---

### Post by spincricket on 2006-06-29
I did update first, but my sources.list looks screwie:

```
fito@mylinux:~$ cat /etc/apt/sources.list

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main
deb-src http://security.ubuntu.com/ubuntu dapper-security main
 deb http://security.ubuntu.com/ubuntu dapper-security universe
 deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Ill fix the sources.list right now and then try waht you suggested.

---

### Post by gingermark on 2006-06-29
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php) if you need a nice reference.

---

