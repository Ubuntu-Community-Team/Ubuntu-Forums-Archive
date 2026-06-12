---
title: "How can I boot with eth0 down?"
date: 2009-03-12
forum: General Help
---

### Post by ForMar on 2009-03-12
> **MaxIBoy said:**
> 

how to have it boot by default with eth0 down


Thats what I want :) 

Thanks in advance 

FYI
- Ubuntu 8.04
- iBook G4 PPC

---

### Post by madverb on 2009-03-12
...the hell you talking about?

---

### Post by MaxIBoy on 2009-03-12
It ought to boot just fine with eth0 down.

If you're asking how to have it boot by default with eth0 down, that is probably in your initscripts. 
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
Try grepping through /etc/init.d for the command "ifup."


Warning! Don't screw around with your initscripts unless you know what you are doing AND you have backed up any files you plan to change.

---

### Post by ForMar on 2009-03-12
> **MaxIBoy said:**
> 

If you're asking how to have it boot by default with eth0 down, that is probably in your initscripts. 

That is what I'm asking :)
> **MaxIBoy said:**
> Warning! Don't screw around with your initscripts unless you know what you are doing AND you have backed up any files you plan to change.
I have no idea what I'm doing but where is the fun if I do :)

---

### Post by ForMar on 2009-03-12
Wells it seems my lack of knowledge has forced me to ask for more help I given the info that MaxIBoy gave me I still cant seem to get it to "boot by default with eth0 down". Any suggestions? 

Thanks for your help btw!

---

### Post by MaxIBoy on 2009-03-12
The initscripts are "shell scripts." A shell script is exactly like the commands you type in a terminal, only instead you type them all at once into a file and just run the file whenever you need those commands. The idea was originally that it saves you the trouble of typing out all those commands over and over, but it is also usable as a simple programming lanugage. 

To know how to edit a shell script, you need to learn how to use the command line.

Basic guide:
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)
Intermediate guide:
[http://tille.garrels.be/training/bash/](http://tille.garrels.be/training/bash/)
Advanced guide (goes into shell scripting more:)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)



Once you've learned this stuff, then you can start messing around with your initscripts.



Remember, those scripts are in charge of getting things set up properly every time you boot. If you do a bad job editing them, you can render your system unbootable. (Usually you can fix it from a liveCD, but sometimes you can screw things up much more permanently.)



Regarding the specific changes you need to make, try grepping through the initscripts for the "ifup" command:
```
 grep -r ifup /etc/init.d
```
Or the "ifconfig" command:
```
 grep -r ifconfig /etc/init.d
```

---

