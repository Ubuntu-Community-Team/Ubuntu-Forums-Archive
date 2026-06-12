---
title: "some help PLEASE"
date: 2010-05-25
forum: Desktop Environments
---

### Post by Ba7r on 2010-05-25
H!

I need some help in the fonts issue, I need to install some fonts like microsoft fonts specially tahoma, I tried to follow the others steps but in vain I couldn't reach anything :confused:

Regards
Muhammed

---

### Post by hok00age on 2010-05-25
> **Ba7r said:**
> H!

I need some help in the fonts issue, I need to install some fonts like microsoft fonts specially tahoma, I tried to follow the others steps but in vain I couldn't reach anything :confused:

Regards
Muhammed 

Method 1 (need Internet access):
Run:
```
sudo apt-get install msttcorefonts
```

Method 2 (have font files in your computer):
```
cd $HOME && mkdir .fonts
```
```
cp /fontdir/fontname.ttf ~/.fonts && fc-cache -f -v
```
Replace /fontdir/fontname.ttf with your font collections path.
Hope this will help you.

---

### Post by Ba7r on 2010-05-25
I did install this package " [msttcorefonts ]("http://google-yahoo-user.blogspot.com")" and It's okay but this happens when I try to write the next codes 

muhammed@ubuntu:~$ sudo apt-get install msttcorefonts
[sudo] password for muhammed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ttf-mscorefonts-installer instead of msttcorefonts
ttf-mscorefonts-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
muhammed@ubuntu:~$ cd
muhammed@ubuntu:~$ cd home &&mkdir .fonts
bash: cd: home: No such file or directory
muhammed@ubuntu:~$ home &&mkdir .fonts
No command 'home' found, did you mean:
 Command 'hose' from package 'netpipes' (universe)
 Command 'tome' from package 'tome' (multiverse)
home: command not found
muhammed@ubuntu:~$ ^C
muhammed@ubuntu:~$

---

