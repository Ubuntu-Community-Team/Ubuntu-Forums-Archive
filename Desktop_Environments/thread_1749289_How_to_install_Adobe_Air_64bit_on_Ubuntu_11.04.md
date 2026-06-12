---
title: "How to install Adobe Air 64bit on Ubuntu 11.04?"
date: 2011-05-04
forum: Desktop Environments
---

### Post by Consecrated on 2011-05-04
Hello,

Can someone explain how to install Adobe Air on Ubuntu 11.04? I am trying to install [Focus Booster]("http://www.focusboosterapp.com/"). I can't understand the [Adobe Instruction]("http://kb2.adobe.com/cps/521/cpsid_52132.html")s and I can't understand the [Jamesward instructions]("http://www.jamesward.com/2010/10/14/install-adobe-air-on-64-bit-ubuntu-10-10/comment-page-1/#comments"). I barely understand how to use terminal. Please explain with detailed terminal instructions. (Assume I downloaded the package into the /home/username/downloads file.)

> To install the Adobe AIR .deb package on a 64-bit system just follow these steps:

Download the [AdobeAIR.deb]("http://get.adobe.com/air/") file
In a terminal window go to the directory containing the adobeair.deb file

Create a tmp dir:
mkdir tmp

Extract the deb file to the tmp dir:
dpkg-deb -x adobeair.deb tmp

Extract the control files:
dpkg-deb --control adobeair.deb tmp/DEBIAN

Change the Architecture parameter from “i386&#8243; to “all”:
sed -i "s/i386/all/" tmp/DEBIAN/control

Repackage the deb file:
dpkg -b tmp adobeair_64.deb

Now you can install Adobe AIR on a 64-bit system! From the command line just do:
sudo dpkg -i adobeair_64.deb

Thanks

---

### Post by zerwas on 2011-05-09
[LIST=1]
[*]Go to [http://get.adobe.com/air/](http://get.adobe.com/air/) and choose the version ".bin".
[*]Go to your Downloads folder, rename the downloaded file from .bin to .sh so it looks like this:

AdobeAIRInstaller.sh
[*]Now right click the file -> Properties -> Permissions and check the last option "Execute as an application".
[*]Click on the file and follow the instructions. From now on, you can click on any .air file to install it.
[/LIST]

---

### Post by pendragyn on 2011-05-10
I an pretty newbish myself but this is what worked for me:

get into a terminal. go to the downloads directory by typing:

cd Downloads

my folder has a capital D, seems to be the standard. my prompt then changed to something ending with ~/Downloads$

Next you can left click and highlight the lines listed in the previous post (one at a time) and paste them into the terminal by right clicking in the terminal by the cursor and selecting paste, then hitting enter. You should get another prompt after hitting enter. You won't get any messages if things go right until the last one with sudo, that should ask you for your password. After that you will get a message about how 32-bit isnt supported etc... After the prompt comes back, it should be installed and you can close the terminal if you're done.

Good luck.  :)

---

### Post by Hyperion_1984 on 2011-05-16
Very strangely, the .bin installer didn't work for me (zerwas' method). It used to work on 10.04 and 10.10. I also tried:

```
sudo dpkg -i --force-architecture adobeair.deb
``` without success.
It results in some dependency problems (libgtk2.0-0 (>= 2.6), libxslt1.1., libxml2.)

I have all those libraries installed. Should I install the 32 bits versions?

---

### Post by sgtGarcia on 2011-05-16
Try this ppa:

[https://launchpad.net/~dajhorn/+archive/adobeair]("https://launchpad.net/~dajhorn/+archive/adobeair")

This is repacked for 64bit Ubuntu.

---

### Post by Hyperion_1984 on 2011-05-18
Thanks SgtGarcia for the suggestion, but it didn't work. The ppa doesn't have files for natty, so I tried installing the Maverick version. I have the same errors with the ppa than with the force architecture option.

---

### Post by Hyperion_1984 on 2011-05-19
I've found a solution here:
[http://ubuntuforums.org/showthread.php?t=1758944]("http://ubuntuforums.org/showthread.php?t=1758944")

---

### Post by Xime1008 on 2011-05-22
> **Consecrated said:**
> Hello,

Can someone explain how to install Adobe Air on Ubuntu 11.04? I am trying to install [Focus Booster]("http://www.focusboosterapp.com/"). I can't understand the [Adobe Instruction]("http://kb2.adobe.com/cps/521/cpsid_52132.html")s and I can't understand the [Jamesward instructions]("http://www.jamesward.com/2010/10/14/install-adobe-air-on-64-bit-ubuntu-10-10/comment-page-1/#comments"). I barely understand how to use terminal. Please explain with detailed terminal instructions. (Assume I downloaded the package into the /home/username/downloads file.)



Thanks
WOW! Thank you VERY MUCH. This instructions really worked!!!! Very nice. A HUGE hug.

---

### Post by Xime1008 on 2011-05-22
> **Consecrated said:**
> Hello,

Can someone explain how to install Adobe Air on Ubuntu 11.04? I am trying to install [Focus Booster]("http://www.focusboosterapp.com/"). I can't understand the [Adobe Instruction]("http://kb2.adobe.com/cps/521/cpsid_52132.html")s and I can't understand the [Jamesward instructions]("http://www.jamesward.com/2010/10/14/install-adobe-air-on-64-bit-ubuntu-10-10/comment-page-1/#comments"). I barely understand how to use terminal. Please explain with detailed terminal instructions. (Assume I downloaded the package into the /home/username/downloads file.)



Thanks
WOW. This instructions worked wonders!! Thank you _very much_.

---

### Post by z61t on 2011-05-27
> **zerwas said:**
> [LIST=1]
[*]Go to [http://get.adobe.com/air/](http://get.adobe.com/air/) and choose the version ".bin".
[*]Go to your Downloads folder, rename the downloaded file from .bin to .sh so it looks like this:

AdobeAIRInstaller.sh
[*]Now right click the file -> Properties -> Permissions and check the last option "Execute as an application".
[*]Click on the file and follow the instructions. From now on, you can click on any .air file to install it.
[/LIST]
This worked for me.  Thanks!

---

### Post by unapendeza on 2011-06-02
I am currently running 64-bit Ubuntu 11.04 (amd64 kernel) and I used the following steps successfully.

1. Install 32-bit library support
```
 sudo apt-get install ia32-libs lib32nss-mdns
```2. Get Adobe Air from the Adobe Air website
 ```
wget -c [http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin](http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin)
``````
md5sum AdobeAIRInstaller.bin 
```3. Set the installer to executable because it is a self-installer

```
chmod +x AdobeAIRInstaller.bin
``````
readelf -d AdobeAIRInstaller.bin
```You'll get an output that reads "Dynamic section at offset 0xd00044 contains 24 entries" and it will list said entries.

4. Install it as root

```
sudo ./AdobeAIRInstaller.bin
```The installation window should pop up. 
And you're done!

---

### Post by mdbarton on 2011-08-30
Thanks unapendeza - worked perfectly!

---

### Post by RobHam06 on 2012-05-21
Additional information to unapendeza's post,  for Ubuntu 64bit 12.04

Install the missing dependency libhal-storage1

```
sudo apt-get install libhal-storage1 
```


If it is missing on your system install libgnome-keyring0

```
sudo apt-get install libgnome-keyring0 
```


Fix the installer issue where it cannot find libgnome-keyring.so (note that this seems to an issue only with the installer and not with the Adobe Air Program once installed)

```
cd /usr/lib

sudo ln -s x86_64-linux-gnu/libgnome-keyring.so.0 libgnome-keyring.so.0 
```


Follow unapendeza's instructions to install AdobeAIRInstaller.bin


The sim link created to libgnome-keyring.so.0 can safely be deleted after installing AdobeAIRInstaller.bin


```
sudo rm /usr/lib/libgnome-keyring.so.0 
```

---

