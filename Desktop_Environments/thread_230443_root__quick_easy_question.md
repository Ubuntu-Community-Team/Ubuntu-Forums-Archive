---
title: "root?  quick easy question"
date: 2006-08-05
forum: Desktop Environments
---

### Post by njzillest on 2006-08-05
i've just reinstalled ubuntu. I created a user named njzillest, hoping it would be granted root privelages. 

For somereason it isnt. and i have to sudo everything. I tried to add user root, but it said only root can do that. I never created a root account. 

It does say i have a root acct named root, but how can i access it? is there a password that is automatically assigned to root? 

```

njzillest@njzillest-laptop:~$ sudo adduser root
Password:
adduser: The user `root' already exists.
njzillest@njzillest-laptop:~$ passwd root
passwd: You may not view or modify password information for root.

```

thanks in advance

---

### Post by 23meg on 2006-08-05
The best way to use root privileges in most cases is sudo. To enable the root account, which is disabled by default, you need to do ```
sudo passwd root
```Disclaimer: don't do it. Use sudo.

---

### Post by cptnapalm on 2006-08-05
One compromise method is to execute:  sudo su

This will ask for your password then as long as you are still on the commandline, you will be root, but without activating a root password per se.

---

### Post by VK2XCI on 2006-08-06
> **23meg said:**
> The best way to use root privileges in most cases is sudo. To enable the root account, which is disabled by default, you need to do ```
sudo passwd root
```Disclaimer: don't do it. Use sudo.

Why such paranoia :confused: 

If there is one reason to abondon Ubuntu and return to Mandriva it will be the "Root User" policy. :mad:

---

### Post by Jagot on 2006-08-06
[https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d](https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d)

---

### Post by 23meg on 2006-08-06
> **VK2XCI said:**
> Why such paranoia :confused: 

If there is one reason to abondon Ubuntu and return to Mandriva it will be the "Root User" policy. :mad:
Once you enable root with the method I and others don't recommend, how will things be different from Mandriva? I haven't used Mandriva but I'm guessing there will be no difference.

---

### Post by aussie.ian on 2006-08-06
On the subject of root user in Gnome, how do I get root access to edit files (open filemanager as root). I've just installed Ubuntu on another partition with Kubuntu. I want to edit Grub so I can boot either but don't know how to open the filemanager to have root access. In KDE this is quite simple you click on file manager superuser mode and enter your password. How do I do this in Gnome???????

---

### Post by ardchoille on 2006-08-06
> **23meg said:**
> Once you enable root with the method I and others don't recommend, how will things be different from Mandriva? I haven't used Mandriva but I'm guessing there will be no difference.

When someone tries to break into your computer, they know there is a root account. If the root account is disabled, it's much more difficult for them to break into it and they can't break into the user accounts because they don't know the which users to break into. I have used Ubuntu since Hoary and I have never needed to actually log into the root account, sudo will work for all command line apps and gksudo will work for all gui apps. There is really no need to enable the root account.

---

### Post by ardchoille on 2006-08-06
> **aussie.ian said:**
> On the subject of root user in Gnome, how do I get root access to edit files (open filemanager as root). I've just installed Ubuntu on another partition with Kubuntu. I want to edit Grub so I can boot either but don't know how to open the filemanager to have root access. In KDE this is quite simple you click on file manager superuser mode and enter your password. How do I do this in Gnome???????

You can open the file manager as root with: gksu nautilus

But, be careful with a root nautilus window, you can easily screw the entire system.

---

### Post by 23meg on 2006-08-06
> **aussie.ian said:**
> On the subject of root user in Gnome, how do I get root access to edit files (open filemanager as root). I've just installed Ubuntu on another partition with Kubuntu. I want to edit Grub so I can boot either but don't know how to open the filemanager to have root access. In KDE this is quite simple you click on file manager superuser mode and enter your password. How do I do this in Gnome???????
```
gksudo nautilus
```will give you a root Nautilus.

You may also find [this trick]("http://www.ubuntuforums.org/showthread.php?t=24008") useful.

---

