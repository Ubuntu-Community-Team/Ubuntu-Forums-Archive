---
title: "dpkg interrupted"
date: 2007-10-30
forum: Desktop Environments
---

### Post by ht1834 on 2007-10-30
I installed ubuntu 7.10 allowing partition program to shrink an existing xp install partition. I entered you tube in firefox and was informed that I needed plug ins to make the movies work. when I tried to down load the plugins the system hung up. after shutdown and restart    , every time i try to download in synaptic, or add remove I get message ( e: dpkg was interrupted you must manually run dkpg --configure -a) to correct problem, and ( e:_cache-> open () failed please report). I am new to ubuntu, and I have been working on this for three days, I have read many posts and researched as much as I know to research. Most posts say to run dpkg -- configure -a and that will fix problem.
When I run dpkg in terminal with sudo, I get,
Setting up flash plugin-nonfree (9.0.48.0.2+really0ubuntu12)
downloading...
--18:27:54--http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
install _flash_player_9_linux.tar.gz
Resolving fp download.macromedia.com 1.0.0.0
connecting to fp download.Macromedia com.1.0.0.0
:80......
Then connection times out and it starts again.
I saw a post from tv that had the exact same problem as this, and he was told to go to bug report, and not get upset. I went to bug report and found no help on this exact problem.
 One post said to do
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
Problem is when I do sudo dpkg --configure -a, it goes into loop as mentioned above.
Question, does anyone know of a fix for this, or must I do clean install, and start over?
Question 2 If I do a clean install will I end up with same problem again right away, or worse yet months down the road?
Thanks

---

### Post by aysiu on 2007-10-30
Maybe try ```
sudo apt-get -f install
```

---

### Post by ht1834 on 2007-10-30
I have tried (sudo apt-get -f install), after entering password I get

e: dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem.

Any other ideas, I could sure use the help.

Thanks

---

### Post by Prospero2006 on 2007-10-30
Are you operating behind a proxy server?
Pros

---

### Post by ht1834 on 2007-10-31
Sorry, Im not sure what a proxy server is, or how to find out if I am running behind one.

---

### Post by taurus on 2007-10-31
Try

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ht1834 on 2007-10-31
When I enter sudo dpkg --configure -a , it tries to connect to fp download then says failed connection timed out then tries again. I cannot enter any further commands. The only way to get out of the terminal is close it. Im sure there must be a fix or combination here that I am not seeing though. I will give it another day for any other ideas, before doing a complete reinstall.
                                       Thanks

---

### Post by ht1834 on 2007-10-31
Does anyone know if a way exists to uninstall then reinstall synaptic package manager, and if there is a chance that could solve my problem?

---

### Post by galois1811 on 2007-12-14
I've met the same problem with you, I think it must be a bug,

I used a proxy to connect to the Internet,and have set the proper proxy IP and port on the plane of "Synaptic package manager",also I can install nearly all the update packages and software except for "flash player".

when I install the "flash player" in firefox, It showed"connecting to  fpdownload.macromedia.com",as it had took a long time, I had forced to quit,and restarted the system.

After that ,when I restart,all the status is the same with "#1" described.and I've also searched lots of resolution on the Internet,but they all didn't work.

I also want to know that is there any method to reinstall the "Synaptic package manager"??or change the URL of flash player referenced in the program? I think the URL of flash player might incorrect or unavailable. :confused:

---

