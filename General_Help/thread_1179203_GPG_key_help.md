---
title: "GPG key help"
date: 2009-06-05
forum: General Help
---

### Post by mohd on 2009-06-05
Hi , am new to ubuntu and i had problem regarding sound , i ran into topics about something called Medibuntu , the topic said that i should add command line at the terminal -*which is easy* , and a GPG key which i donno what or where that is 

the topic is here 'https://help.ubuntu.com/community/Medibuntu'

am using the new ubuntu 9.04

---

### Post by chriskin on 2009-06-05
just use the command that is said there for the key

or did i understand something wrongly?

---

### Post by chriskin on 2009-06-05
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update


to avoid any misunderstanding

---

### Post by Soul-Sing on 2009-06-05
synaptic: medibuntu-keyring: enable/install

---

### Post by mohd on 2009-06-05
Sorry guys i didn't understand

it says i should add this 'sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list'

and this 'sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update' 

are both of them added to the terminal ?

---

### Post by chriskin on 2009-06-05
yep
you just write each one on the terminal and press enter, write your password and you are ok :)

---

### Post by mohd on 2009-06-05
Ok , do you know about that problem when you plug in the headphones in the laptop , and you hear sound from the speakers as well ??

edit , i get that error when i add the 2nd command

E: Malformed line 47 in source list /etc/apt/sources.list (dist parse)

---

### Post by chriskin on 2009-06-05
can you post here the line it talks about?


also for the sound problem , god help you to solve it

jaunty solved it for me, all the previous versions had it

search the forums, you will find hundreds of posts on the topic

---

### Post by mohd on 2009-06-05
this one
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

the 1st one works fine , but this gives me the error i mentioned above

also i tried to install mediabuntu from here 'http://packages.medibuntu.org/jaunty/medibuntu-keyring.html' after downloading the file when i try to use it it gives me a msg 

'software index is broken 
this is a major failure of your software management system.please check the broken packages with synaptic ,check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

note that i put that line as it is 'sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update' i donno if these && mean i should use it as parts

and what is jaunty ?

---

### Post by chriskin on 2009-06-05
jaunty is your version of ubuntu, IF it really is that :P 

might you be using an older version, thus getting errors trying to make it work for jaunty?


also, i meant if you can send the sources.list , so i can see where the error is

---

### Post by mohd on 2009-06-05
oh lol , umm guess that should be it i just downloaded it yesterday

but am sorry i don't know how to send the list ?

if you mean whats written in the terminal window 
"mohammed@mohammed-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
--2009-06-05 18:57:55--  [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 280 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 280         --.-K/s   in 0s      

2009-06-05 18:57:56 (13.9 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [280/280]"

and then after that i add the 2nd command i told you about and i get the erorr


sorry for causing you much trouble

---

### Post by chriskin on 2009-06-05
go to /etc/apt/*sources*.*list* and open it, and send the text here
then i can see why it says that a line is malformed

---

### Post by mohd on 2009-06-05
i didn't know where to put that , i used it in the web browser i got that

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) jaunty restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) jaunty-security restricted main universe #Added by software-properties
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main
deb [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

---

### Post by chriskin on 2009-06-05
ok now

open the terminal 
and write
sudo gedit /etc/apt/sources.list

write your password 

and change the last line with
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

it seems that you made some kind of mistake with the commands of the wiki, probably typed something wrong or ... i don't know, the important thing is that this line is wrong and the one i posted is the correct one, or so i think at least (almost 100% sure)

---

### Post by mohd on 2009-06-05
Thanks very much , guess it worked fine 
got some errors in the end but they seem normal

i really appreciate your patience , and thanks again

---

### Post by chriskin on 2009-06-05
if you need anything on the subject, post and i will reply as soon as possible

---

### Post by mohd on 2009-06-05
Donno if this is related , i tried to install Avidemux 

look at that photo here

[IMG]http://i42.tinypic.com/2d7y1i9.png[/IMG]

---

### Post by Soul-Sing on 2009-06-05
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free 
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

replace the old medibuntu lines in your sources.list with these above.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

-----------------------------------------------------------------

[COLOR="Red"]or remove them from your sources.list[/COLOR]

go to system: managment: software sources: third party software:
add: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free 
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
reload your sources.

ad the keyring: synaptic: medibuntu-keyring: install.

and your done.

---

