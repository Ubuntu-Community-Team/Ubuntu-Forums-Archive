---
title: "Ubuntu studio 9.04 crashes while installing openoffice.org mailmerge"
date: 2009-05-02
forum: General Help
---

### Post by ludwigg77 on 2009-05-02
HI All, I set up a Ubuntu Studio 9.04 system recently, dual boot with Vista which was originally installed on my PC. 
  I tried installing  OpenOffice.org using the standardadd/remove application and t always stops at the following line:   Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...
 This takes the whole system down, and we have to do a hard reboot. After restarting we cannot install any upgrades or new packages before continuing the old installation. If we run, as proposed by the updater:
   dpkg --configure -a
 the openoffice.org-emailmerge installation is continued but, again, hangs and takes the system down at exactly the same line.
 Please tell me which further information you need to resolve this issue.
Any help is much appreciated. 

Cheers, 

Greg

---

### Post by 300Z on 2009-05-02
Hi, I'm in the exact same position as you... and still haven't been able to fix it. :(
[My unanswered thread.]("http://ubuntuforums.org/showthread.php?p=7198476#post7198476")

Leo

---

### Post by ludwigg77 on 2009-05-02
HI Leo, 
Thanks for your note,  I have been unable to solve this issue so far...
Let me know if you fin a nice trick. 
Any body out there who can assist?
Cheers, 
Greg

---

### Post by 300Z on 2009-05-03
Just did a clean reinstall of Studio but didn't install open office this time and so far things are looking good.

Leo

---

### Post by ludwigg77 on 2009-05-05
Hi There, 
Thanks for advising. I also tried that, there is no issues with the OS till openoffice is being installed. 
Let me know the progress, I haven't been succesfull so far...
Any body out there who has a clue for this thread?
Cheers, 
Greg

---

### Post by ludwigg77 on 2009-05-09
Hi Leo, 

Any luck with openoffice?

Did reinstall of the whole machine but openoffice freezes the computer, even if I install only 1 component of it (ie spreadsheet etcc..)
Let me know. 
cheers, 
Greg

---

### Post by 300Z on 2009-05-09
Hi Greg,

I haven't bothered to install Open Office on this machine since I don't really need it... I can use Open Office on my other regular Ubuntu 8.10 drive if I have need it. :)

---

### Post by c10 on 2009-05-11
Same problem here, locks completely up when trying to install that mailmerge.py file from within ubuntu studio 9.04.

---

### Post by 300Z on 2009-05-11
Yeah I'm afraid this is a conflict with the Studio OS. :(

---

### Post by nartu on 2009-05-12
Hello, my jaunty J ubuntu studio freezes while installing open office... I finally can launch ubuntu again but got no more access to synaptic... 
sudo dpkg --configure -a does not work, and freezes the os too, so what can I do to unlock synaptic?
thanks to you all, nartu.

---

### Post by 300Z on 2009-05-12
I think you most likely will have to reinstall the OS... at least that was the only solution for me...

---

### Post by poloking on 2009-05-14
Do you think it might be a problem with the new realtime kernel

Im not sure but i thought I would throw it out there.

---

### Post by 300Z on 2009-05-14
No idea... :(

---

### Post by KoalaMan on 2009-05-15
Exactly the same problem for me, same OS, same messages...

Hope a reinstall will fix the problem, and that I will keep in mind that OOo should not be installed on Studio... I'll use Vista instead for office needs! :lolflag:

---

### Post by c10 on 2009-05-16
I found a command on another thread

sudo dpkg -r openoffice.org

which seems to work for me (at least I don't get Synaptic locking up on me).
Hopefully there is a fix on the way...

---

### Post by talkeetnik on 2009-05-19
Had the same problem . After a complete reinstall left off the mailmerge package and ooffice seems to be okay. (At least at this point in time)

Will beat it up a little and see if I can lock-up the system again.

An alternate safe-boot or non-rt kernel might be an interesting test.

whb

---

### Post by king dumb on 2009-05-20
I can confirm the same [jaunty sudio vs oOO]

Seems it is a conflict with the RT Kernel alright,

this fix the issue for me 
```

sudo rm /var/lib/dpkg/info/openoffice.org-emailmerge.prerm
sudo dpkg -r --force-all openoffice.org-emailmerge
```

The is a bug listed here and a fix:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/368570")

***king Dumb

---

### Post by chitek on 2009-05-21
Man I've been waiting for an answer to this.  The problem now is that I don't know how or what kernel to install and also I am not sure about the repositories for openoffice.org.  I openoffice is an option in add/remove programs does that mean that I have the repositories installed?

---

### Post by poloking on 2009-05-21
Yes I can confirm this is a fix

All you need do is type in the terminal:
```
sudo apt-get install linux-generic
```

This will install the generic kernel. Then reboot your computer and at the boot menu move to the one which ends wtih "generic" instead of "rt". Boot into that system.

When the system loads up, use synaptic, the add/remove application or type in a terminal:
```
sudo apt-get install openoffice.org
```

Then reboot and be sure to use the "rt" system kernel when doing anything ubuntu-studio ish. Have fun!

---

### Post by nartu on 2009-05-25
> **poloking said:**
> Yes I can confirm this is a fix

All you need do is type in the terminal:
```
sudo apt-get install linux-generic
```

This will install the generic kernel. Then reboot your computer and at the boot menu move to the one which ends wtih "generic" instead of "rt". Boot into that system.

When the system loads up, use synaptic, the add/remove application or type in a terminal:
```
sudo apt-get install openoffice.org
```

Then reboot and be sure to use the "rt" system kernel when doing anything ubuntu-studio ish. Have fun!

Many thanks for the trick, open office is running, but
synaptic gave that message after the install process:

E: openjdk-6-jre-headless: le sous-processus post-installation script a retourné une erreur de sortie d'état 2
E: icedtea-6-jre-cacao: problèmes de dépendances - laissé non configuré
E: openjdk-6-jre: problèmes de dépendances - laissé non configuré
E: ttf-kannada-fonts: le sous-processus post-installation script a retourné une erreur de sortie d'état 2
E: ttf-oriya-fonts: le sous-processus post-installation script a retourné une erreur de sortie d'état 2
E: ttf-telugu-fonts: le sous-processus post-installation script a retourné une erreur de sortie d'état 2

does anybody know the way to solve this issue?
thanks to you all, nartu.

---

### Post by c10 on 2009-07-18
I would think Ubuntu Studio users would need the real-time kernel (at least those using audio applications) than Open Office, the fix above might not be the best.

---

### Post by welshmike on 2009-07-19
I am now running 9.10 and it does not freeze.

---

### Post by 1wang on 2009-10-29
> **poloking said:**
> Yes I can confirm this is a fix 

All you need do is type in the terminal:
```
sudo apt-get install linux-generic
```This will install the generic kernel. Then reboot your computer and at the boot menu move to the one which ends wtih "generic" instead of "rt". Boot into that system.

When the system loads up, use synaptic, the add/remove application or type in a terminal:
```
sudo apt-get install openoffice.org
```Then reboot and be sure to use the "rt" system kernel when doing anything ubuntu-studio ish. Have fun!

It is only necessary to use the above genric kernel for the installation of Openoffice-writer with synaptic. After successfull installaton I was able to work with Openoffice Writer with the Ubuntu 9.04 Studio real time kernel. So my summary on what to do is.

1.) remove the mailmerge install programm, which makes srrews up the package managment
2.) Deinstall all Openoffice components
3.) Install the generic kernel
3.) Boot on the generic kernel
4.) Install openoffice with the generic kernel
5.) Boot on the real time kernel
6.) You can use Openoffice

( I tried it only with Openoffice-Writer from [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main )

For details see all the thrad above in this thread and other posts about the setup of the right authentification keys for  [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

best regards from

1wang

---

### Post by tehowe on 2009-10-29
So... has the problem with OpenOffice installs trashing the UbuntoStudio package manager been resolved with Karmic? Anyone know?

---

### Post by 1wang on 2009-11-25
Solution: No problems any more with Openoffice installation on ubuntu studio 9.10 clean installation
-------------------------------------------------------------------------------------------------------------------------
I updated from Ubuntu studio 9.04 with the Ubuntu 9.10 (not studio) repository. I had already two kernels. After the upgrade I had four kernels but only one worked. So after some other crazy things I decided to format and do a clean new installation of Ubuntu studio 9.10
In the Openoffice installation I saw some workaround, which delays the installation or setup of the Openoffice Mailmerge packet to a later time in the installation process. In the end I as an user had no problems with the Openoffice Suite.

PS: remarks to the upgrade from Ubuntu 9.04 studio to Ubuntu 9.10 studio
--------------------------------------------------------------------------------------------
from Ubuntu 9.04 studio to Ubuntu 9.10 studio a lot of things have changed, which made me some troubles:
I started ubuntu 9.04 via chainloading from an older grub, which I had installed with a red hat installation. But ubuntu 9.10 had changed to grub 2 (1.97~beta4-1ubuntu4). Chainloading from the older to the newer grub did not work or I did not find out how to do it. My solution was to start Redhat from the newer grub 2 from Ubuntu, which worked.  But now chances, that an update of Red Hat will brake my Multiboot system is increased. So I would prefer Chainloading.
Annother problem was the password input with the stylus of my wacom tablet on my notebook IBM X41 tablet. I was able to work completely without the keyboard. To type in text or passwords I used on screen keyboards with the stylus. But from Ubuntu 9.04 to 9.10 setups have changed a lot. I still cannot type in my password with the stylus for screen unlock (see my post: [http://ubuntuforums.org/showthread.php?t=1320426](http://ubuntuforums.org/showthread.php?t=1320426)). I am lucky. I can turn my display and still us the keyboard. But what are people doing, who have only tablet?

---

### Post by mudzakkir on 2010-04-20
Hi, friends.. I have the same problem. I have post my problem in this <a href"http://ubuntu-indonesia.com/forums/ubbthreads.php/topics/8878#Post8878">link</a> but I am not get a good response or a good problem solving. Can you give me the tutorial or article to resolving my problem? please guide me to resolving my problem. I am a Jaunty user, but I dont want to upgrade my OS to other Ubuntu version. I just need the problem solving. My open office is not working, and when I install any application, the mail merge is appears and not responding. I have been install linux generic, and boot into other kernel, but my problem still not solved.
Help me. I dont want to uninstall my jaunty. i just need the way to fix this problem...

---

