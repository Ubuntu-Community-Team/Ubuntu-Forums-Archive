---
title: "Cannot install new fonts"
date: 2010-11-14
forum: Desktop Environments
---

### Post by UTF16 on 2010-11-14
I'm using Ubuntu 10.10. I followed twice the following instructions: [http://ubuntuforums.org/showthread.php?t=85139](http://ubuntuforums.org/showthread.php?t=85139)
and
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) (manual)

in order to install fonts that worked perfectly under previous Ubuntu releases. The new fonts don't appear in any of applications I tried.

---

### Post by stinkeye on 2010-11-14
Do the fonts show up in
Appearance > fonts
If you only need to make the fonts available to you and not other uses
you can just place them in ~/.fonts.
Create the **.fonts ** folder in your home directory if you don't have one.

---

### Post by UTF16 on 2010-11-14
Yes, but in no application, like OpenOffice, Windows programs run through Wine, Gedit, Firefox etc. How do I make them recognize?

---

### Post by stinkeye on 2010-11-14
> **UTF16 said:**
> Yes, but in no application, like OpenOffice, Windows programs run through Wine, Gedit, Firefox etc. How do I make them recognize?
Appearance > fonts and change the application and/or document fonts.
Don't know about ooffice or wine programs though.

---

### Post by UTF16 on 2010-11-14
It doesn't matter those fonts show up in system applications; from my point of view they are not installed, since I can't use them. It seems like the font installation is being made more and more difficult with every Ubuntu release. How can such a trivial task be so complicated?

---

### Post by oldos2er on 2010-11-14
You may need to update your font cache ```
sudo fc-cache -fv
```

---

### Post by fabio.hipolito on 2011-06-09
Hi, I had a similar problem was in the font files. If you copy your fonts from a hd partition or usb-drive formatted in fat or ntfs, the permissions are lost. Consequently the programs wont have access to the files, for me the solution was simple, I just had to reset the permissions.

Make sure that your font files  have the correct permissions, so I looked at ubuntu fonts for an example. Open a terminal and move to the ubuntu-font-famil and list the files
```
nebulosa@strix:~$ cd /usr/share/fonts/truetype/ubuntu-font-family/
nebulosa@strix:/usr/share/fonts/truetype/ubuntu-font-family$ ll
total 2252
drwxr-xr-x  2 root root   4096 2011-04-26 07:00 ./
drwxr-xr-x 21 root root   4096 2011-06-09 12:11 ../
-rw-r--r--  1 root root 362784 2011-03-09 00:46 Ubuntu-BI.ttf
-rw-r--r--  1 root root 339320 2011-03-09 00:46 Ubuntu-B.ttf
-rw-r--r--  1 root root 415424 2011-03-09 00:46 Ubuntu-LI.ttf
-rw-r--r--  1 root root 421172 2011-03-09 00:46 Ubuntu-L.ttf
-rw-r--r--  1 root root 389744 2011-03-09 00:46 Ubuntu-RI.ttf
-rw-r--r--  1 root root 359668 2011-03-09 00:46 Ubuntu-R.ttf
```
my font files did not had the r permission, so I had to add r permission to my files
```
sudo chmod +r font1.ttf font2.ttf
```

Best regards.

---

