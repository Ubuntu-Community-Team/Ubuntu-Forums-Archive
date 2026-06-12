---
title: "Help with xbmc media center installation"
date: 2009-04-05
forum: General Help
---

### Post by Nick01 on 2009-04-05
IF SOMEONE HAS AN IDEA ON HOW TO INSTALL THE XBMC MEDIA CENTER ON MY COMPUTER, PLEASE HELP ME STEP BY STEP BECAUSE I WENT  TO THE How to Install XBMC Media Center In Ubuntu Hardy WEBSITE, I DID WHATEVER IT SAYS BUT I GOT NOTHING. WHY? SOMEONE PLEASE HELP

---

### Post by xfearxnxloathing on 2009-06-19
bump..  i added the site to source list, got the ppa key and followed instructions and i got nothing just a bunch of xbmc files and nowhere to go..  cant ./configure, make, make install...  =[

---

### Post by Mack1 on 2009-06-21
This worked perfectly for me on ubuntu 9.04, 3 mins install in total:

add this key via the terminal:
gpg --no-default-keyring --keyring /tmp/tmp.keyring --keyserver keyserver.ubuntu.com --recv 91E7EE5E && gpg --no-default-keyring --keyring /tmp/tmp.keyring --export --armor 91E7EE5E | sudo apt-key add - && rm /tmp/tmp.keyring

type in terminal:
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

Go to third parties software and click add, type this in:
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) jaunty main 

(for hardy type in hardy in stead of jaunty)

Click close, click reload

in terminal type:
Sudo apt-get install xbmc

eh voila, done!

You can start xbmc through the ubuntu menu under video or:
xbmc in terminal

have fun!

---

### Post by MarcusA on 2009-07-04
> **Mack1 said:**
> 
in terminal type:
Sudo apt-get install xbmc

eh voila, done!

I get bash: Sudo: command not found at this step.

---

### Post by Quazza on 2009-07-07
Hi MarcusA,

Did you type it exactly as Mack1 posted it as I noticed he used a capital S when in actual fact the command should be lower case.

So try the same command but use a lower case 's' 

```
sudo apt-get install xbmc

```

Cheers Quazza :D

---

