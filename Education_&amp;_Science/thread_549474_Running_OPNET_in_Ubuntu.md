---
title: "Running OPNET in Ubuntu?"
date: 2007-09-12
forum: Education &amp; Science
---

### Post by rmccabe3701 on 2007-09-12
I just got an OPNET license for my research and I was looking though the "system requirements" portion of the installation instructions.  It said the the only supported Linux platforms are Fedora and Red Hat.  I was just wondering if anyone has installed OPNET on Ubuntu.  If so could you share your experience?  I really don't want to install anoter OS, I really like Ubuntu :(

---

### Post by rmccabe3701 on 2007-09-13
Actually I went ahead and installed OPNET in Ubuntu.  Everything seems to be working alright so far.  Here's what I did to install:

[http://decision.csl.uiuc.edu/~rmccabe2/opnet_sim.html]("http://decision.csl.uiuc.edu/~rmccabe2/opnet_sim.html")

---

### Post by faali on 2009-06-23
> **rmccabe3701 said:**
> Actually I went ahead and installed OPNET in Ubuntu.  Everything seems to be working alright so far.  Here's what I did to install:

[http://decision.csl.uiuc.edu/~rmccabe2/opnet_sim.html]("http://decision.csl.uiuc.edu/%7Ermccabe2/opnet_sim.html")

this link is not working. 
kindly update this link.???

---

### Post by rmccabe3701 on 2009-12-20
I'm not a graduate student at UIUC anymore, so I don't have a computer account there anymore, sorry

---

### Post by Chronon on 2009-12-21
Care to briefly describe what you did then?  (alien, I'm guessing)

---

### Post by rmccabe3701 on 2009-12-21
I don't remember doing anything out of the ordinary -- I think I even followed OPNET's install instructions for Red Hat.  As I recall, the Ubuntu Opnet install was somewhat buggy in that OPNET would crash periodically and there was a massive memory leak.  At the time I was running version 12 or 13 (I forget which), I know there is a version 15 out now, maybe they fixed this problem.  Sorry I don't remember much more, it was 2 years ago.

---

### Post by aloumvrios on 2010-05-13
alright, i'm new to ubuntu and id like to install opnet 15.0.A.
So i've tried a couple of times doing this procedure

i)sudo apt-get install g++ csh

ii)then i added
PATH=$PATH:/usr/opnet/15.0.A/sys/unix/bin
export PATH
in /etc/bash.bashrc
saved (as root ofc)

iii)wrote bash in terminal to reload the file

iv)installed the bins (modeler, docs, models)

so installation completed with no failures or warnings...
but when i try to run the modeler it says tha op_set_env does not exist. also many opnet files inside the bin are broken
I tried the same procedure to another pc and the same happened...
any ideas?

---

### Post by mariosx on 2011-05-05
> **aloumvrios said:**
> alright, i'm new to ubuntu and id like to install opnet 15.0.A.
So i've tried a couple of times doing this procedure

i)sudo apt-get install g++ csh

ii)then i added
PATH=$PATH:/usr/opnet/15.0.A/sys/unix/bin
export PATH
in /etc/bash.bashrc
saved (as root ofc)

iii)wrote bash in terminal to reload the file

iv)installed the bins (modeler, docs, models)

so installation completed with no failures or warnings...
but when i try to run the modeler it says tha op_set_env does not exist. also many opnet files inside the bin are broken
I tried the same procedure to another pc and the same happened...
any ideas?

(old threat i know..)

has anyone tried to run it through WINE ?

---

