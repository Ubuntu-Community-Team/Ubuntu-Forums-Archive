---
title: "some newbie questions"
date: 2005-07-24
forum: Desktop Environments
---

### Post by tuokor on 2005-07-24
Hi, just installed kubuntu.I had tried ubuntu but it just felt so clumsy so I decided to try kubuntu. MAN :grin:   this is great it's fast and solid as a rock but for newbie guy I have a few questions.

1.Where is the firewall or doesn't linux need one?

2.How do I install ati drivers, the screen looks ok but I have heard that 3d doesn't work without installing them. Also what I have read in different forums that it's little hard to install?

3.How can I see my other partitions? I see these icons about them but when I click the icon KDE says that error "mount: /dev/hda6 is'nt found in /etc/fstab or in /etc/mtab" what does this mean? I have read little about linux so I know that that hda6  is the partition in a linux way. But what do i need to do so i can access that partition it's a NTFS partition?

4.How can I change the login screens resolution? changed the resolution from kde to right but in the login screen the resolution is wrong where do i change that?

5. How do ad more time to the grub bootloader 10 seconds isn't enough?

---

### Post by DJ_Max on 2005-07-24
1.) I don't have one on my computer, but I have one on my server(shorewall). If you want one for your personal computer, there's one built in, but to interface it, try firestarter.

2.) [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

3.) [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by tuokor on 2005-07-25
Thanks found answer to all questions except question number 4!!!
How can i change the resolution in the login screen it's always 1024x1200 but I want it to be 1024x768 in KDE it's ok but the damn login screen jumps to wrong res everytime :-x

---

### Post by bored2k on 2005-07-25
[QUOTE=tuokor]Thanks found answer to all questions except question number 4!!!
How can i change the resolution in the login screen it's always 1024x1200 but I want it to be 1024x768 in KDE it's ok but the damn login screen jumps to wrong res everytime :-x[/QUOTE]
 4. Inside a terminal, type:
```
sudo dpkg-reconfigure xserver-xorg
```
There, make sure you uncheck the resolutions you don't want for your screen. After you're done, reboot your computer and it's feel good time :D.

5. Go to [http://bored2k.cjb.net/](http://bored2k.cjb.net/) . Download Grubconf. Installing by issuing the
```
sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb
```command on it. Then to launch it type sudo grubconf. The first time you open it the application WILL crash, so just close it and restart again. There you can painlessly configure your boot screen (watchout editing boot lines though).

---

### Post by ltmon on 2005-07-25
Another good (and more KDE based) firewall config tool is guarddog, which is in Universe.

L.

---

### Post by Terracotta on 2005-07-25
I tried guarddog once, and  the result was that I couldn't connect to the internet anymore, even after I uninstalled it (and even rebooted since uninstall didn't solve it) I couldn't get on the internet, how come? the other pc in this house has zonealarm which does the job fine, I'd like to install a firewall here, but what do I have to take in mind to configure it proper? The internet connectiong is just cable, and it's configured with dhcp, could that be the problem?

---

### Post by bored2k on 2005-07-25
[QUOTE=Terracotta]I tried guarddog once, and  the result was that I couldn't connect to the internet anymore, even after I uninstalled it (and even rebooted since uninstall didn't solve it) I couldn't get on the internet, how come? the other pc in this house has zonealarm which does the job fine, I'd like to install a firewall here, but what do I have to take in mind to configure it proper? The internet connectiong is just cable, and it's configured with dhcp, could that be the problem?[/QUOTE]
 What about Firestarter ?

---

