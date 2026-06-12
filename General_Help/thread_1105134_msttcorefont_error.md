---
title: "msttcorefont error"
date: 2009-03-24
forum: General Help
---

### Post by imparja2 on 2009-03-24
I'm not sure what I should do to fix this error msttcorefont is reported to be responsible for my computer crashing at least three times a day.

I got this message when I tried to upgrade 

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

what should I do next?

---

### Post by Bachstelze on 2009-03-24
Try

```
sudo dpkg --configure -a
```

---

### Post by imparja2 on 2009-03-24
I used this command before and that's how I discovered there was an error here what else can I try?

I don't even know what msttcorefont, why I need it or why it's causing the problem can I reinstall or delete it?  please tell me how

thanks

---

### Post by imparja2 on 2009-03-24
I tried using the command you gave me and got this

Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts

I hope this makes it easier to identify my problem

---

### Post by sky911 on 2009-12-09
To solve the problem you must do such a thing:

Open Termial and write:
luk@ubuntu:~$ sudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

In this script you must comment some lines(see the pictures 1 and 2) :

db_get msttcorefonts/http_proxy
http_proxy=$RET
export http_proxy

After that save changes and install one more:
luk@ubuntu:~$ sudo apt-get install msttcorefonts 

It' would be a success install.

---

### Post by sky911 on 2009-12-09
[Russian Edition]
&#1044;&#1083;&#1103; &#1088;&#1077;&#1096;&#1077;&#1085;&#1080;&#1103; &#1101;&#1090;&#1086;&#1081; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1099;

&#1054;&#1090;&#1082;&#1088;&#1086;&#1081;&#1090;&#1077; &#1090;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083; &#1080; &#1085;&#1072;&#1087;&#1077;&#1095;&#1072;&#1090;&#1072;&#1081;&#1090;&#1077;:
luk@ubuntu:~$ sudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

&#1042; &#1101;&#1090;&#1086;&#1084; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090;&#1077; &#1085;&#1072;&#1076;&#1086; &#1079;&#1072;&#1082;&#1086;&#1084;&#1084;&#1077;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1090;&#1100; &#1090;&#1088;&#1080; &#1089;&#1090;&#1088;&#1086;&#1082;&#1080; (&#1089;&#1084;&#1086;&#1090;&#1088;&#1080; &#1082;&#1072;&#1088;&#1090;&#1080;&#1085;&#1082;&#1080; 1 &#1080; 2) :

db_get msttcorefonts/http_proxy
http_proxy=$RET
export http_proxy

&#1055;&#1086;&#1089;&#1083;&#1077; &#1101;&#1090;&#1086;&#1075;&#1086; &#1089;&#1086;&#1093;&#1088;&#1072;&#1085;&#1080;&#1090;&#1077; &#1080;&#1079;&#1084;&#1077;&#1085;&#1077;&#1085;&#1080;&#1103; &#1080; &#1079;&#1072;&#1087;&#1091;&#1089;&#1090;&#1080;&#1090;&#1077; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1103;&#1094;&#1080;&#1102; &#1089;&#1085;&#1086;&#1074;&#1072;:
luk@ubuntu:~$ sudo apt-get install msttcorefonts 

&#1042; &#1080;&#1090;&#1086;&#1075;&#1077; &#1076;&#1086;&#1083;&#1078;&#1085;&#1072; &#1073;&#1099;&#1090;&#1100; &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1072;&#1103; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1103;&#1094;&#1080;&#1103;.

---

### Post by norville on 2010-02-12
Open Termial and write:
luk@ubuntu:~$ sudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

... but why I have not this file on my computer?

---

