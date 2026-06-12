---
title: "what am I doing wrong"
date: 2009-04-14
forum: General Help
---

### Post by woop on 2009-04-14
Im new to ubuntu and need help 
everytime I copy this into terminal 
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

from[]("https://help.ubuntu.com/community/Medibuntu")

the terminal runs through a lot of stuff then 

I get a message towards the end
 
Fetched 11.9kB in 1s (8841B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

as above what am I doing wrong 
prob something simple as Im new here



I also seem to be having problems with nvidia driver it just stays at 0% downloading

---

### Post by overdrank on 2009-04-14
Hi and try using the command given ```
sudo dpkg --configure -a
```

---

### Post by woop on 2009-04-14
cool thanks for the help, I did and its changed to

Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I did try apt-get -f 
however 4 entries came up
The program 'apt' can be found in the following packages:
 * openjdk-6-jdk
 * cacao-oj6-jdk
 * sun-java5-jdk
 * sun-java6-jdk
I presume these are what Ive already tried to get..............totally lost
I think its because i tried to use the medibutu repository but all is gone wrong now
I get a broken package notification when I enter synaptic
anyone have a link to a good guide to starting ubuntu eg. sorting youre driver, setting up repositories, etc

---

### Post by nothingspecial on 2009-04-14
You need to sudo it.

```
sudo apt-get -f install
```

Also type it exactly, spaces and everything.

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by jmszr on 2009-04-14
woop,

       This sticky by umg6hr is an excellent place to start: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404). I would suggest the Free Ubuntu Pocket Guide by Keir Thomas and Psychocats Ubuntu Guide as of particular interest but the entire thread is full of good information.

---

### Post by woop on 2009-04-14
> **nothingspecial said:**
> You need to sudo it.

```
sudo apt-get -f install
```

Also type it exactly, spaces and everything.

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
 I believe I tried to run before I could walk hence I will use the link provided, thanks

it worked!!
thank you nothingspecial from an Irish linux user
love the sig

I now have another problem whenever I go into synaptic I get a broken package notification, I in my infinite wisdom deleted it and cannot fix it now
any ideas?
cheers

---

### Post by nothingspecial on 2009-04-14
> **woop said:**
> 

I now have another problem whenever I go into synaptic I get a broken package notification, I in my infinite wisdom deleted it and cannot fix it now
any ideas?
cheers

What have you deleted?

---

### Post by woop on 2009-04-14
it was related to medi ubuntu and I found it under the broken package title in synaptic
cant remember exactly what it was either way I want to know how to get rid of the broken package notification
as its not allowing me to get any new software

the help is much appreciated

---

### Post by nothingspecial on 2009-04-15
Do 
```
sudo apt-get -f install
```

again and post the output please.

---

### Post by woop on 2009-04-17
hi just getting back to this now
was in windows land for a day or two
here you go
anthony@anthony-desktop:~$ sudo apt-get -f install
[sudo] password for anthony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anthony@anthony-desktop:~$

---

### Post by woop on 2009-04-17
ok weird just ran synaptic and all is well 
quite odd
Ive got a nvidia geforce 7300 cant get it working...............I think Ill constantly be asking questions

---

