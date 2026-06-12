---
title: "preferences???"
date: 2005-09-19
forum: Desktop Environments
---

### Post by tasulo on 2005-09-19
I am new to KUbuntu so forgive me if i seem slow, i am trying to get the backport repositories downloaded and when i get to the part at the beginning where you have to do the:   _sudo cp -f preferences /etc/apt/_ all i get is "can not stat `preferences': no such file or directory." How in the world do i fix this problem, Any help would be greatly appreciated, Thank you so much.

---

### Post by drizek on 2005-09-19
[QUOTE=tasulo]I am new to KUbuntu so forgive me if i seem slow, i am trying to get the backport repositories downloaded and when i get to the part at the beginning where you have to do the:   _sudo cp -f preferences /etc/apt/_ all i get is "can not stat `preferences': no such file or directory." How in the world do i fix this problem, Any help would be greatly appreciated, Thank you so much.[/QUOTE]
 you can just skip that step if you want. all it does is backup the file.

its just a precaution, and it is highly unlikely that anything will go wrong. but if it does, you can just post here and well help you fix it ;)

---

### Post by tasulo on 2005-09-19
[QUOTE=drizek]you can just skip that step if you want. all it does is backup the file.

its just a precaution, and it is highly unlikely that anything will go wrong. but if it does, you can just post here and well help you fix it ;)[/QUOTE]
 ok, i skipped that step, i got all the way through it. when i got to the end and typed this:
_sudo apt-get update_         I got this
_E: Opening /etc/apt/sources.list - ifstream: :ifstream (2 no such file or directory)_

---

### Post by tasulo on 2005-09-19
Someone please help me with this problem, i can't open Kynaptic or Synaptic becasue of it, thank you.

---

### Post by Freddy on 2005-09-19
I don't know whats wrong but maybe you can print out your conf file for apt.get in here.  /// Freddan

---

### Post by drizek on 2005-09-19
open /etc/apt/sources.list in a text editor and post it here.

---

### Post by tasulo on 2005-09-19
[QUOTE=drizek]open /etc/apt/sources.list in a text editor and post it here.[/QUOTE]
 i would but i honestly don't know how, whenever i try to do anything all i get is:   "cannot stat" `xxxxxxxxx'   no such file or directory??

---

### Post by drizek on 2005-09-19
[QUOTE=tasulo]i would but i honestly don't know how, whenever i try to do anything all i get is:   "cannot stat" `xxxxxxxxx'   no such file or directory??[/QUOTE]
 just go to /etc/apt in konqueror and then just click on sources.list

---

### Post by Freddy on 2005-09-19
Open up your console and write "kwrite /etc/apt/sources.list" if you have kwrite installed, don't use sudo just yet, only for root buisness. copy all that you find in there and post it here.  /// Freddan

---

### Post by tasulo on 2005-09-19
[QUOTE=drizek]just go to /etc/apt in konqueror and then just click on sources.list[/QUOTE]
 deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


ok, i believe this is it, i did it exactly how you said, thank you.

---

### Post by drizek on 2005-09-19
[QUOTE=tasulo]deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


ok, i believe this is it, i did it exactly how you said, thank you.[/QUOTE]
 replace it with this:



#deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

