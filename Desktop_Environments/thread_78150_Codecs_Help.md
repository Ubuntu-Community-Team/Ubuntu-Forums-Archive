---
title: "Codecs Help? ?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Fern_azul10 on 2005-10-17
I was able to install all the codecs I needed except for 2 which were the w32codecs & libdivx4linux everytime I try to install the through the terminal I get this message Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
 or
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libdivx4linux
is their another way to install these codecs or am I doing it wrong the commands Im using are in the old guide

sudo apt-get install w32codecs

sudo apt-get install libdivx4linux
Please Help!!!!!!!!!!!!!!!!!!

---

### Post by cdhotfire on 2005-10-17
[quote=Fern_azul10]I was able to install all the codecs I needed except for 2 which were the w32codecs & libdivx4linux everytime I try to install the through the terminal I get this message Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
 or
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libdivx4linux
is their another way to install these codecs or am I doing it wrong the commands Im using are in the old guide

sudo apt-get install w32codecs

sudo apt-get install libdivx4linux
Please Help!!!!!!!!!!!!!!!!!![/quote]

same here, but from my experience they seem to be pre-installed.  i might be wrong on this, but all movies ive tried work perfectly.:)

---

### Post by Murgle on 2005-10-17
I know for a fact the the w32 codecs are not officially supported by ubuntu for legal resons but a quick through the forums for the w32 codecs gave me this link to a site with a deb for it

[QUOTE=mcduck]You could also get win32 codecs with 
'wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb'
..and..
'sudo dpkg -i w32codecs_20050412-0.0_i386.deb'[/QUOTE]

hope this helps with the w32codecs you can also probably find another link for the other in the forums

---

### Post by dbott67 on 2005-10-17
[QUOTE=Fern_azul10]is their another way to install these codecs or am I doing it wrong the commands Im using are in the old guide

sudo apt-get install w32codecs

sudo apt-get install libdivx4linux
Please Help!!!!!!!!!!!!!!!!!![/QUOTE]

Add the following line to the end of your /etc/apt/sources.list file:
```
deb ftp://ftp.nerim.net/debian-marillat/ sarge main
```
Download the w32codecs and then remark out the repository, as it can cause major issues if you leave it enabled during an upgrade.
```
# deb ftp://ftp.nerim.net/debian-marillat/ sarge main
```

-Dave

---

### Post by Antman on 2005-10-17
[QUOTE=Fern_azul10]I was able to install all the codecs I needed except for 2 which were the w32codecs & libdivx4linux everytime I try to install the through the 
Please Help!!!!!!!!!!!!!!!!!![/QUOTE]

[See here]("http://ubuntuforums.org/showthread.php?t=75579&highlight=w32codecs")

---

### Post by chinaski on 2005-10-19
[QUOTE=Murgle]I know for a fact the the w32 codecs are not officially supported by ubuntu for legal resons but a quick through the forums for the w32 codecs gave me this link to a site with a deb for it



hope this helps with the w32codecs you can also probably find another link for the other in the forums[/QUOTE]
thank you!:p

---

