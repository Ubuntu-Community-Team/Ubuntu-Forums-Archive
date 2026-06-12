---
title: "2 Problems I need help with."
date: 2008-12-03
forum: General Help
---

### Post by DaveGiant on 2008-12-03
Hi there, 

2 issues.

The first issue is that I tried to install some updates and one failed. I think it was described as broken. When I ran it I was asked to find it using the something filter. Could someone tell me how I remove this update so I can download it again and hopefully install it correctly?

The second issue is with a network driver. I am prompted to download and install the Broadcom B43 Wireless Driver. I click on the prompt. Click on activate. It starts to download and install. It gets to 61%, then the progress bar starts to go crazy, there is a progress bar block about a 1/5 of the size of the whole bar and it just jumps around the bar.

I currently cannot connect to any wireless networks and assume this driver will help things. I am hoping that installing all the updates will fix this. I was just wondering if any one knew why it was getting stuck and going 'funny' at 61%.

---

### Post by fooman on 2008-12-03
i think you will need to fix issue #1 before you will be able to download and install the wireless driver.

i assume you are connecting through an ethernet cable for now...correct?

in a terminal,  run the following command and post the output back here so we can see where the update is failing:

```
sudo apt-get update
```

if that goes without an error,  run this one and post the output:

```
sudo apt-get upgrade
```

---

### Post by DaveGiant on 2008-12-03
Here is the output.

> jason@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  openoffice.org-style-andromeda: Depends: openoffice.org-common (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-style-crystal: Depends: openoffice.org-common (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-style-human: Depends: openoffice.org-common (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-style-tango: Depends: openoffice.org-common (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
E: Unmet dependencies. Try using -f.


---

### Post by fooman on 2008-12-03
do you have the universe and multiverse repositories enabled in synaptic?

open synaptic (system > administration > synaptic package manager) and in the toolbar click settings > repositories.

on the ubuntu software tab...make sure that the first 4 options are checked then try to update again.

---

### Post by DaveGiant on 2008-12-03
Thanks so much. I don't think I quite did what you said. I went to the filters -> Broken section. 

From here I am not sure what happened at all to be honest, I think open office was removed because the package was broken but at the same time the network drivers were installed. Don't know how or why but suddenly I have wireless and the 30 metre networking cable snaking through my house can be removed. 

Thanks!

---

