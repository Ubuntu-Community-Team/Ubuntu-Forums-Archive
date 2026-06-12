---
title: "Eternal lands on ubuntu?"
date: 2012-05-14
forum: Gaming &amp; Leisure
---

### Post by Someonesappinmylinux on 2012-05-14
looked at Eternal Lands on playdeb and tried to install it useing the apt-get method but i get this error: End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /var/cache/eternallands/el_linux_193.zip or
        /var/cache/eternallands/el_linux_193.zip.zip, and cannot find /var/cache/eternallands/el_linux_193.zip.ZIP, period.
dpkg: error processing eternallands-data (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 eternallands-data
W: Duplicate sources.list entry [http://ppa.launchpad.net/pjbroad/ppa/ubuntu/](http://ppa.launchpad.net/pjbroad/ppa/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_pjbroad_ppa_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
.



I have no clue what that means. any advice for a ubuntu noob?

---

### Post by Trlberdrcem on 2012-05-15
That's interesting and nice.
Yeah.
:guitar:
[IMG]http://i.imgur.com/3oWMV.gif[/IMG]











___________________________________________________________
[SIZE=1]Do not anticipate trouble or worry about what may never happen.Keep in the [five fingers]("http://www.cheapvibramfivefingerssale.net")[/SIZE]

---

### Post by Sableyes on 2012-05-15
> **Someonesappinmylinux said:**
> 
W: Duplicate sources.list entry [http://ppa.launchpad.net/pjbroad/ppa/ubuntu/](http://ppa.launchpad.net/pjbroad/ppa/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_pjbroad_ppa_ubuntu_dists_oneiric_main_binary-i386_Packages)


Suggests you have multiple entrys of the same line, similiar error here : 

[http://askubuntu.com/questions/120621/w-duplicate-sources-list-entry-http-archive-ubuntu-com-ubuntu-precise-update](http://askubuntu.com/questions/120621/w-duplicate-sources-list-entry-http-archive-ubuntu-com-ubuntu-precise-update)

The secound reply explains how to remove a duplicate entry in the sources list. Follow them instructions, but do it for :

 [http://ppa.launchpad.net/pjbroad/ppa/ubuntu/](http://ppa.launchpad.net/pjbroad/ppa/ubuntu/)

Not the partners repository. See if that helps.

---

### Post by Someonesappinmylinux on 2012-05-15
thankyou kindly

---

### Post by Someonesappinmylinux on 2012-05-15
sigh, now im getting an error message of :

sudo [/var/cache/eternallands/el_linux_193.zip]: command not found
 after running the 'sudo dpkg --configure -a' command it says to input after it wont open. it cant find a   /var/cache/eternallands/el_linux_193.zip.zip
and even the prepackages install from [https://help.ubuntu.com/community/EternalLands](https://help.ubuntu.com/community/EternalLands) comes up with the same error

---

