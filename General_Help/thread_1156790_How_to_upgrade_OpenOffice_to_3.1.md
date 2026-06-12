---
title: "How to upgrade OpenOffice to 3.1?"
date: 2009-05-12
forum: General Help
---

### Post by AlNaimi on 2009-05-12
Hi every one....
I'm using ubuntu 9.04 with OpenOffice 3.0
How could i upgrade it to OpenOffice 3.1?
Thanks a lot in advanced

---

### Post by konqueror7 on 2009-05-12
1. Edit your sources.list
```
sudo gedit /etc/apt/sources.list/CODE]
2. Paste the following entry
[CODE]
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main

```
3. Issue the following commands
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
[URL="https://launchpad.net/~openoffice-pkgs/+archive/ppa"]
OpenOffice PPA[/URL]

or if you want to do a clean install, [here]("http://tektrap.blogspot.com/2009/05/installing-openoffice-31-in.html")

---

### Post by AlNaimi on 2009-05-12
No Words to thank you konqueror7

---

### Post by stinger30au on 2009-05-12
awesome

thanks

---

### Post by kpkeerthi on 2009-05-12
You also need to add the GPG key for the PPA before you run apt-get update
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 247D1CFF 

```

---

### Post by binbash on 2009-05-12
[http://www.ubuntu-inside.me/2009/05/openoffice-31-for-ubuntu.html](http://www.ubuntu-inside.me/2009/05/openoffice-31-for-ubuntu.html)

---

### Post by Arup on 2009-05-19
paste this in terminal, enter your password

echo -e 'echo "#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/ppa.list

gpg --keyserver keyserver.ubuntu.com --recv 247d1cff
gpg --export --armor 247d1cff | sudo apt-key add -

sudo apt-get update

sudo aptitude -y safe-upgrade
sudo aptitude -y dist-upgrade
' > ./oooupgrade.sh
sudo sh ./oooupgrade.sh && rm ./oooupgrade.sh

type yes to all options offered and you will have OO 3.1 after its downloaded.

Thanks goes to dougfractal's post on softpedia guide to OO upgrade.

---

### Post by scouser73 on 2009-05-19
Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the Linux .deb file.

Once you have done that, extract the .deb file, **OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m11_native_packed-4_en-US.9399**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m11_native_packed-4_en-US.9399** onto the desktop then open Terminal and paste this command: [B]sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb
[/B]
Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb**

Once you've done that you'll find OpenOffice 3.1.0 in Office

---

