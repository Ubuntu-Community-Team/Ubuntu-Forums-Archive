---
title: "realplayer is a real problem"
date: 2006-04-12
forum: Desktop Environments
---

### Post by threethirty on 2006-04-12
I cant use apt at all.  as soon as i open up synaptic i get this error 
```
E: The package realplayer needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```
and i get the same thing from the command line.  ive tried to remove it using dpkg -r but nothin.

any ideas?

---

### Post by apjone on 2006-04-12
download
 RealPlayer10GOLD.bin
libstdc++5_3.3.6-8ubuntu1_i386.deb
run 
sudo dpkg -i libstd 
then 
sudo ./realplayer 
and change the l;ocation to /etc/realplayer and select yes to system wide links

---

### Post by apjone on 2006-04-12
the two complete filenames

RealPlayer10GOLD.bin
libstdc++5_3.3.6-8ubuntu1_i386.deb
you will also need build-essentials and gcc3 availible via apt-get

---

### Post by threethirty on 2006-04-12
where is a good place to download libstdc++5_3.3.6-8ubuntu1_i386.deb

and i cant get  build-essentials and gcc3 because I cant use apt-get

---

### Post by apjone on 2006-04-13
open a terminal and type 
'sudo apt-get install -f' this will fix any broken installs you have on your system.
to remove installs and their conf files
'sudo apt-get remove "Application name" --purge


here is a link as well


[http://ubuntu.interlegis.gov.br/archive/pool/main/g/gcc-3.3/](http://ubuntu.interlegis.gov.br/archive/pool/main/g/gcc-3.3/)

that contains the above lib file

---

### Post by threethirty on 2006-04-13
well I've tried 'sudo apt-get install -f' and 'sudo apt-get remove realplayer --purge'

and the both returned:
```
E: The package realplayer needs to be reinstalled, but I can't find an archive for it.
```

---

### Post by Ramses de Norre on 2006-04-13
Are you connected to the internet?
If so try:
sudo apt-get install --reinstall realplayer
If it doesn't work:
sudo apt-get clean && sudo apt-get install --reinstall realplayer
or
sudo apt-get clean && sudo apt-get remove --purge realplayer && sudo apt-get install realplayer

---

