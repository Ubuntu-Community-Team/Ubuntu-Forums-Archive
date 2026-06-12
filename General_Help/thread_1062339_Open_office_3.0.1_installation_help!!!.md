---
title: "Open office 3.0.1 installation help!!!"
date: 2009-02-06
forum: General Help
---

### Post by meinvateristnein on 2009-02-06
i need help installing open office 3.0.1 on ubuntu 8.04.2 i have tried many times with many tuts and no luck

any suggestions would be cool

---

### Post by mb_webguy on 2009-02-06
Open System->Administration->Software Sources.  Click on the Third-Party Software tab.  Click the Add button, and paste the following line in the "APT line" textbox.```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
```
Now right-click and download [this file]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF").  In Software Sources, click on the Authentication tab.  Click the Import Key File button, and locate the file you just downloaded.  Now close Software Sources.  You'll be prompted to update your sources, so do it.

Update Manager may now inform you that updates are available.  If so, you can just run Update Manager to upgrade to OOo3.  If not, open Synaptic and search for openoffice.  Mark the openoffice.org package for installation, then click the Apply button.

Congratulations, you now have OpenOffice 3.

---

### Post by yusuo85 on 2009-02-06
i literally just done this 

firstly do this command in terminal
sudo apt-get remove openoffice*.*

then goto "http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.1" and download the package

when its done unzip it somewhere nice

in terminal go into that folder in my case 
yusuo@media:~$ cd Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/

and simply use this command
sudo dpkg -i *

when its done use
cd desktop-integration/

and use "sudo dpkg -i *" again and you should be done

you must have java installed for this to work 
sudo apt-get install sun-java6-jre

hope this helps

---

### Post by yusuo85 on 2009-02-06
i tried what mb_webguy said before hand and it didnt work for me hence the long way around

---

### Post by mb_webguy on 2009-02-06
Yusuo85's instructions will work to install OpenOffice 3, but you'll have to manually install new versions when they are released.  

If you add the openoffice-pkgs PPA, you will automatically receive updates through Update Manager as they are released.

---

### Post by meinvateristnein on 2009-02-06
thanks to everyone but nothing worked except for yusuo85 method and its funny because i just did that and it didnt work for me ...... the first post is messed everyone does that but it never works for me

---

### Post by mb_webguy on 2009-02-06
*shrug*  It worked for me on three different computers, one of those once with 32-bit and again with 64-bit Intrepid.

---

### Post by meinvateristnein on 2009-02-06
ya but want install on hardy heron ....... i dont know if it works for it but i know it works for ibex

---

### Post by yusuo85 on 2009-02-06
i used to use ibex and yeah mb_webguys method works fine but im on hardy now and the same method didnt work, hence the long way around.
Im glad this helped you meinvateristnein, its a shame mb_webguys method didnt work for us cause now we have to update manually each time

---

### Post by exploder on 2009-02-06
The update feature is enabled in the Sun version. Doesn't the built in update tool work?

---

### Post by callmeray on 2009-02-06
Worked like a champ, mb_webguy, and I'm running 8.04. Added the source and key, reloaded and the update manager immediately popped up with updates.

---

### Post by rasmus91 on 2009-02-07
What do i do to update to newest version in Intrepid?

---

### Post by scouser73 on 2009-02-07
Firstly remove OpenOffice: > sudo apt-get remove openoffice*.*

Visit this site: [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

Download the Linux Deb package to your desktop

Open Terminal and paste the following codes one at a time.

1 - > sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.deb

Once the old version of OpenOffice has been removed, you will be able to install the package that provides menu items for OpenOffice 3.0:

2 - > sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9376_all.deb


You can then go to Office and see that OpenOffice 3.0.1 is installed.

---

