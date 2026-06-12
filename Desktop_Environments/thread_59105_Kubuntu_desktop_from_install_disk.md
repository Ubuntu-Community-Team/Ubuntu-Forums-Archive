---
title: "Kubuntu desktop from install disk?"
date: 2005-08-22
forum: Desktop Environments
---

### Post by earther on 2005-08-22
Right now I have Ubuntu and Kubuntu running on two old boxes.  I saw the thread that gives instructions on how to install Kubuntu desktop on Ubuntu so there is a choice at login.  Unfortunately, I'm on low speed dialup and the estimated time was in double digits!  Is there a way to install Kubuntu desktop from the Kununtu install disk that I burned on a friend's high-speed connection?

Thanks for your help.

---

### Post by SGC on 2005-08-22
Yes there is, open the terminal and type the following command:
```
sudo apt-cdrom add
[ insert kubuntu cdrom and hit enter]
```
After that:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by earther on 2005-08-22
[QUOTE=SGC]Yes there is, open the terminal and type the following command:
```
sudo apt-cdrom add
[ insert kubuntu cdrom and hit enter]
```
After that:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```[/QUOTE]
 Thanks so much.  I figured there was.  The whole Linux thing is quite a learning experience. At least I 'm making progress.

---

### Post by earther on 2005-08-26
[QUOTE=SGC]Yes there is, open the terminal and type the following command:
```
sudo apt-cdrom add
[ insert kubuntu cdrom and hit enter]
```
After that:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```[/QUOTE]Is there a way to install only Konqueror (not the whole KDE desktop) using the install disk?  After much thought, I realized that it would be a better for me to do it this way.  Thanks again.

---

### Post by SGC on 2005-08-26
I didn't try it, But I think you need to replace **apt-get install kubuntu-desktop** with **apt-get install konqueror**. This will give you a minimal kde installition (kdebase, kdelibs, arts)

---

### Post by earther on 2005-08-26
[QUOTE=SGC]I didn't try it, But I think you need to replace **apt-get install kubuntu-desktop** with **apt-get install konqueror**. This will give you a minimal kde installition (kdebase, kdelibs, arts)[/QUOTE]Great!  That confirms what I thought it would be.  Thanks again.

---

### Post by earther on 2005-08-27
[QUOTE=SGC]I didn't try it, But I think you need to replace **apt-get install kubuntu-desktop** with **apt-get install konqueror**. This will give you a minimal kde installition (kdebase, kdelibs, arts)[/QUOTE]
 Just want to report that I now have Konqueror on my Gnome desktop.  Thanks for the help.

---

### Post by 65vitesse on 2006-10-06
hi,

i know this is old so i might not get a reply.

i typed the commands exactly (except from a root terminal)
and it goes off and tries to get it from the internet anyway.

any clues?

---

### Post by kerry_s on 2006-10-06
Open synaptic > settings > repositories and uncheck all the repos except the cdrom.

---

### Post by 65vitesse on 2006-10-07
Hi,

thanks, i tried that but it says can't find kubuntu-desktop.

is this because the install started from the net the first time i tried?

cheers all

---

