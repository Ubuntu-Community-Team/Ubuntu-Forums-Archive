---
title: "Missing files/directories?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-08-09
Well ive been trying to do several things like get my wireless adaptor working and install drivers. I find instructions on this forum telling me to run things using the terminal. When i type in the commands i get an output claiming that there is no such file/directory. In general would this have to do with a kernel update or what? I just get constant failures when following simple instructions on installing system tools just because i cant get the right output in the kernel that everyone else seems to have no problems at all.

Edit: Usually when I install applications i put them into my home folder so installing those such things isnt a problem. But installing system utilities such as bcm43xx-fwcutter i get this type of output:


[I] patrick@patrick-desktop:~$ sudo sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package bcm43xx-fwcutter
patrick@patrick-desktop:~$
[/I]

---

### Post by etank on 2006-08-09
When you run ```
apt-cache search bcm43xx
```does the package show up? You should see this ...```
bcm43xx-fwcutter - Utility for extracting Broadcom 43xx firmware
``` If not then you need to add the universe repo.

---

### Post by maniacmusician on 2006-08-10
^what he said. though if you're a total newbie, i don't know if you know about repositories. to change them, you open synaptic package manager (it's the graphical frontend for the apt-get command you're using), click on settings, repositories. then enable the ones you need. 

but if you're installing your wireless card, then i don't imagine that you have internet on that machine, do you? I have found your "Help with ndiswrapper!!!" page. i will go there now and try to help you out as i have a long history of trouble with that program (usually ending in success). 

cya there.

---

