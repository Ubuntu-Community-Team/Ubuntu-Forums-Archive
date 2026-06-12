---
title: "Strange messages during installation"
date: 2009-05-27
forum: General Help
---

### Post by oakdeveloper on 2009-05-27
Hi,

During the installation of gwget on my Ubuntu 9.04, I got some strange messages which I am posting here. I have highlighted them in red below. Kindly guide me if there is any problem. Please do let me know what those messages mean.

> oakdeveloper@oakbook:~$ sudo apt-get install gwget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gwget
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 228kB of archives.
After this operation, 1376kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe gwget 1.0.1-0ubuntu1 [228kB]
Fetched 228kB in 3s (73.9kB/s)                         
Selecting previously deselected package gwget.
(Reading database ... 165594 files and directories currently installed.)
Unpacking gwget (from .../gwget_1.0.1-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up gwget (1.0.1-0ubuntu1) ...
[COLOR=Red]You must have at least one <locale> entry in a <schema>
You must have at least one <locale> entry in a <schema>
You must have at least one <locale> entry in a <schema>
You must have at least one <locale> entry in a <schema>
You must have at least one <locale> entry in a <schema>[/COLOR]

Processing triggers for menu ...
oakdeveloper@oakbook:~$Thanks,
Babu

---

### Post by pennacook on 2009-05-27
Did you try:
```
cd /usr/share/gconf/schemas
sudo gconf-schemas --register *.schemas
```

---

### Post by oakdeveloper on 2009-05-27
I have tried your suggestion. It gives me the same messages.

```
oakdeveloper@oakbook:~$ cd /usr/share/gconf/schemas/
oakdeveloper@oakbook:/usr/share/gconf/schemas$ sudo gconf-schemas --register *.schemas
You must have at least one <locale> entry in a <schema>
You must have at least one <locale> entry in a <schema>
You must have at least one <locale> entry in a <schema>
You must have at least one <locale> entry in a <schema>
You must have at least one <locale> entry in a <schema>
oakdeveloper@oakbook:/usr/share/gconf/schemas$ 


```

---

