---
title: "How to get back fedora installation which disappeared after ubuntu installation?"
date: 2009-01-19
forum: General Help
---

### Post by mukeshksahu on 2009-01-19
Hi All,

     Two operating system were installed in my desktop PC, WinXP and Fedora - 7. After that I installed ubuntu on same machine by creating 5 gb of unallocated space. Ubuntu installation was successful on it is running without any problem. Now problem is that I have lost my Fedora installation. Now I can see boot menu provided by ubuntu instead of fedora grub boot option. boot menu shows 3-4 boot option for ubuntu ,one for winXP and one for other. I am able to boot my PC to XP but when I go to other option(Which I guess to be Fedora) It shows me some error "string unrecognized" something like that. 

Now my question is that Is there any way to get back fedora installation running along with XP and Ubuntu on same system? 

Waiting for your valuable answer.

Thanks in advance
Mukesh Sahu

---

### Post by Tim Sharitt on 2009-01-19
Grub probably didn't properly detect the fedora installation. You should be able to manually add it to your /boot/grub/menu.lst file.

Post the contents of /boot/grub/menu.lst. It would probably helpful to mount your fedora partition in Ubuntu and post the contents of its menu.lst file.

---

### Post by caljohnsmith on 2009-01-19
You could manually add the Fedora boot entries in Fedora's grub.conf to your Ubuntu menu.lst, but if you do that, you will have to manually update your Ubuntu's menu.lst every time you get a kernel upgrade in Fedora. I would recommend instead using the following entry in your Ubuntu's menu.lst:
```
title Fedora Grub Menu
root (hdX,Y)
configfile /boot/grub/grub.conf
```
And replace (hdX,Y) with the Fedora partition, and also give the correct location of Fedora's grub.conf file if it is different. If you run into problems, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Fedora from Ubuntu.

---

