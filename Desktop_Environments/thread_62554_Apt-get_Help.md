---
title: "Apt-get Help"
date: 2005-09-05
forum: Desktop Environments
---

### Post by karuptdata on 2005-09-05
I am fairly new to ubuntu but not to debian core. I am trying to set up updated reposits, however i am having the hardest time getting this to work anybody know of any updated (gaim kernel) reposits?

---

### Post by celluloid on 2005-09-05
[QUOTE=karuptdata]I am fairly new to ubuntu but not to debian core. I am trying to set up updated reposits, however i am having the hardest time getting this to work anybody know of any updated (gaim kernel) reposits?[/QUOTE]
 I too had this problem. 
Using synaptic though.
I decided to update to 5.10 Breezy with apt-get and edited my sources list, changing all "hoary" to "breezy". 
I also added the hoary backports (i don't think there are breezy backports yet, correct me if wrong)
[www.ubuntuguide.org](www.ubuntuguide.org)

Now my synaptic/apt doesn't get errors anymore and i have a nice system running breezy.
Not sure if this will help you.
Grant.

---

### Post by karuptdata on 2005-09-05
Unfortunately that doesnt help me much forgive my ignorance i need to know how to edit to include debian reposits as well in order to update kernel and several other thing any other suggestions?

---

### Post by wabble on 2005-09-05
[QUOTE=karuptdata]Unfortunately that doesnt help me much forgive my ignorance i need to know how to edit to include debian reposits as well in order to update kernel and several other thing any other suggestions?[/QUOTE]

Not sure if this is what you mean..

Have you uncommented all the # in your sources.lst for apt?

sudo gedit /etc/apt/sources.lst

remove all # in front of all the adresses and add one # to the one that refers to your ubuntu cd rom.

Then type sudo apt-get update and you should be good to go from either synaptics og apt-get i think.

---

### Post by celluloid on 2005-09-05
[QUOTE=karuptdata]Unfortunately that doesnt help me much forgive my ignorance i need to know how to edit to include debian reposits as well in order to update kernel and several other thing any other suggestions?[/QUOTE]
 From my n00b stance, I would think you would need to find some debian repositories and simply add them to your sources.list? sounds pretty simple but i'm not sure if this is the key. 

Sorry I can't be of more help.

---

### Post by smeager on 2005-09-05
[QUOTE=celluloid]From my n00b stance, I would think you would need to find some debian repositories and simply add them to your sources.list? sounds pretty simple but i'm not sure if this is the key. 

Sorry I can't be of more help.[/QUOTE]
I would be very careful adding any repositories that aren't specifically built for ubuntu. You may end up breaking your system. (Trust me I know). Almost anything you need will be in the Ubuntu repositories (if you have them all) main restricted universe multiverse.

---

### Post by karuptdata on 2005-09-05
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

# deb-src [http://packages.debian.org/unstable](http://packages.debian.org/unstable)
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb [http://ubuntu.nooms.de/hoary/](http://ubuntu.nooms.de/hoary/)


that is what reposits are listed in the sources.list i dont think that its correct any way to correct this?

---

