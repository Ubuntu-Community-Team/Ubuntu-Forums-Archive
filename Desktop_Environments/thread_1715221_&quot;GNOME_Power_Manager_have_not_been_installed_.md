---
title: "&quot;GNOME Power Manager have not been installed correctly&quot; - still no fix"
date: 2011-03-26
forum: Desktop Environments
---

### Post by XmaX on 2011-03-26
This morning, my Ubuntu froze, and I had to hard-restart. Upon reboot, i got the warning message that "The configuration defaults for GNOME Power Manager have not been installed correctly". I googled for a bit and tried many methods: freeing up some disk space, reinstalling power manager, reinstalling ubuntu-desktop, sudo dpkg --configure -a, chmod 0777 /tmp, mkdir /var/lib/gconf/default - all with no luck. In the end, I got the system back and running by installing Xfce... but the error message still pops up in Xubuntu. Also, so far I've noticed that the Update Manager crashes when I try to update.

Anyone has any ideas of how to fix it? I want my GNOME desktop back! :)

---

### Post by Krytarik on 2011-03-26
I did a quick web search about it, some findings point in the direction of nearly used up disk space. Did you check that? How much disk space do you have free in the root partition?

---

### Post by XmaX on 2011-03-26
> **Krytarik said:**
> I did a quick web search about it, some findings point in the direction of nearly used up disk space. Did you check that? How much disk space do you have free in the root partition?
I only have one partition, and I currently have over 1 GB free. I had around 500 MB for a long time without any problems.

---

### Post by bssennoga on 2011-04-07
Nice People,

I have had this problem for a month or so, so please forgive my frustration n exasperation if it shows up in my posts:

System: Ubuntu 10.04.1 Server, on Dell Optiplex330. Webmin+Squid+ an apt-mirror.

I have tried the following and still failed:
1. chmod 1777 /tmp (and its variants) - i notice, there is an orbit-gdm that is owned by gdm:gdm. 
2. shorter password
3. reinstalling gdm
4. large amounts of sudo apt-get update && sudo apt-get upgrade followed by sudo reboot
5. have also tried:

[I]proxyadmin@proxy:~$ /usr/lib/libconf-2-4/gconf-sanity-check-2
-bash: /usr/lib/libconf-2-4/gconf-sanity-check-2: No such file or directory
proxyadmin@proxy:~$ /usr/lib/libconf2-4/gconf-sanity-check-2
-bash: /usr/lib/libconf2-4/gconf-sanity-check-2: No such file or directory[/I]

 and its intended solution: 
*sudo mkdir -p /usr/local/etc/gconf/gconf.xml.defaults*

This server (squid + mirror) is hosting crucial services and i really need to get it working. I need anyone who can wrap their head around this to help. Am attaching what necessary files - 

please skype me (bssennoga) and also, help me understand if there is anything like: 10.04 Server 64-bit LiveCD!!! and where to get it.

stranded & frustrated, but ready to learn.

---

### Post by Krytarik on 2011-04-07
> **bssennoga said:**
> 
```
proxyadmin@proxy:~$ /usr/lib/libconf-2-4/gconf-sanity-check-2
-bash: /usr/lib/libconf-2-4/gconf-sanity-check-2: No such file or directory
proxyadmin@proxy:~$ /usr/lib/libconf2-4/gconf-sanity-check-2
-bash: /usr/lib/libconf2-4/gconf-sanity-check-2: No such file or directory

```
Please check the filesystem of the root partition:
```
sudo touch /forcefsck
```
This will force a check upon the next boot.

---

