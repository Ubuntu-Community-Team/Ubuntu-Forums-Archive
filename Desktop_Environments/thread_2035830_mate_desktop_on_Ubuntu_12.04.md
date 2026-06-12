---
title: "mate desktop on Ubuntu 12.04"
date: 2012-07-31
forum: Desktop Environments
---

### Post by geordiejohn on 2012-07-31
hello i have got Ubuntu 12.04 and gnome classic desktop and i was wondering how i can install the Mate desktop to try please ?
Thank you.

---

### Post by garyzw on 2012-07-31
To install MATE 1.2 open a Terminal and enter the following one line at a time--pressing enter after each line

sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main"
sudo apt-get update 
sudo apt-get install mate-archive-keyring 
sudo apt-get update 
sudo apt-get install mate-core 
sudo apt-get install mate-desktop-environment

---

### Post by geordiejohn on 2012-07-31
hello i did as you said but it did not work,i did it twice,here is what i saw at the first error-


Err [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise Release.gpg     
  Unable to connect to packages.mate-desktop.org:http:
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise Release
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Sources/DiffIndex
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main i386 Packages/DiffIndex
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main TranslationIndex
Err [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Sources
  Unable to connect to packages.mate-desktop.org:http:
Err [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main i386 Packages
  Unable to connect to packages.mate-desktop.org:http:
Err [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Translation-en_GB
  Unable to connect to packages.mate-desktop.org:http:
Err [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Translation-en
  Unable to connect to packages.mate-desktop.org:http:
W: Failed to fetch [http://packages.mate-desktop.org/repo/ubuntu/dists/precise/Release.gpg](http://packages.mate-desktop.org/repo/ubuntu/dists/precise/Release.gpg)  Unable to connect to packages.mate-desktop.org:http:

W: Failed to fetch [http://packages.mate-desktop.org/repo/ubuntu/dists/precise/main/source/Sources](http://packages.mate-desktop.org/repo/ubuntu/dists/precise/main/source/Sources)  Unable to connect to packages.mate-desktop.org:http:

W: Failed to fetch [http://packages.mate-desktop.org/repo/ubuntu/dists/precise/main/binary-i386/Packages](http://packages.mate-desktop.org/repo/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to packages.mate-desktop.org:http:

W: Failed to fetch [http://packages.mate-desktop.org/repo/ubuntu/dists/precise/main/i18n/Translation-en_GB](http://packages.mate-desktop.org/repo/ubuntu/dists/precise/main/i18n/Translation-en_GB)  Unable to connect to packages.mate-desktop.org:http:

W: Failed to fetch [http://packages.mate-desktop.org/repo/ubuntu/dists/precise/main/i18n/Translation-en](http://packages.mate-desktop.org/repo/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to packages.mate-desktop.org:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by geordiejohn on 2012-07-31
i think mate are having trouble because i saw this-

Important:
We are experiencing difficult with packages.mate-desktop.org. During the update process, if you encounter connection problems, please use repo.mate-desktop.org instead of packages.mate-desktop.org/repo/. Also, please note that it is repo.mate-desktop.org and NOT repo.mate-desktop.org/repo/. If you are a Linux Mint user and make this change, remember to change /etc/apt/preferences as well.

---

### Post by garyzw on 2012-07-31
I installed MATE last night on another PC and it worked then-- maybe try again later.

---

### Post by geordiejohn on 2012-07-31
thank you i will keep trying now i know the sudo commands.

---

### Post by garyzw on 2012-07-31
You are trying to install to Ubuntu 12.04 right?

---

### Post by houseworkshy on 2012-07-31
The commands have a good built in referance, just type man in front of any of them to get to the command manual page.  
"sudo" is a command in itself which escalates the privalages of whatever follows it to root powers.   It's one command which is best used only when it has to be,  which happens to be often; installs and big system changes will all want it.
It is wise, after useing it, to follow with a "sudo -k" ( which terminates those privelages early ) especially if browsing, as the escalated privalages are on a 15 minet timer.

I know this is an aside but  " ... the sudo commands"  suggested that it might be a timely one.

---

### Post by Frogs Hair on 2012-08-01
Make sure the computer is updated prior to adding the repository and try again. The repository information appears to be up to date based on the instructions I have found .

---

### Post by garyzw on 2012-08-01
The MATE website has detailed install instructions

[http://mate-desktop.org/install/](http://mate-desktop.org/install/)

---

