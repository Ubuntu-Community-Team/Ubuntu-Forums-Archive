---
title: "install gnome"
date: 2008-02-27
forum: Desktop Environments
---

### Post by ispy on 2008-02-27
I have Xubuntu here that i want to make Ubuntu. how do I install JUST gnome?

the reason i ask is because i installed KDE on my other partition and now it hates me because i can't get rid of it... i used apt-get instead of aptitude...

but if i just want Gnome and not the apps that come with Ubuntu, what do i get?

---

### Post by sstusick on 2008-02-27
Just download the Ubuntu CD here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) 

Ubuntu = Just Gnome
Kubuntu = Just KDE
Xubuntu = Just XFCE

---

### Post by ispy on 2008-02-27
umm, i'd rather not go through wit a whole installation, how do i install Gnome so i can choose it at login as my session?

---

### Post by sstusick on 2008-02-27
In the terminal: sudo apt-get install ubuntu-desktop.

---

### Post by ispy on 2008-02-27
right, that's what i did on my other partition, but i'm switching to this one so the other can be just storage until my external hdd comes, but that's not the point... i just want GDM.

can i "sudo aptitude install gdm"?

---

### Post by ispy on 2008-02-27
sorry if i'm not clear. let me spell out what happened to me...

i installed Ubuntu... and I love it... but i installed Xubuntu on a small, backup partition just in case something happened to my Ubuntu Partition, which it did... and now Gnome is messed up... so i want to install Gnome on my Xubuntu so i can choose which one i want at the login screen.

i try synaptic, and I get a huge list of programs and i'm not sure which one i need, because i see a lot of dependencies i don't want... I just want GNOME....

if anyone knows the magic code to make this work, let me know...

thanks!!!

---

### Post by sstusick on 2008-02-27
Can you log into Xubuntu? if so, put this into the terminal: sudo apt-get install ubuntu-desktop. Once Gnome is installed, boot into it, and then in the terminal, type sudo apt-get remove xubuntu-desktop.

---

### Post by ispy on 2008-02-27
yes, i'm in it right now

and i can get into Ubunto too, but i want to use this partition and start over on a clean install

and Ubuntu-desktop installs dependencies. I just want Gnome, not the default Ubuntu Apps...

---

### Post by sstusick on 2008-02-27
I have no idea how you would do that, sorry. 

I have searched the forums and found nothing. Hopefully will come along and be able to help.

---

