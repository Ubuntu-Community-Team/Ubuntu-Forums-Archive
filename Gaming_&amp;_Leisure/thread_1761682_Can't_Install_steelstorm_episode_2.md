---
title: "Can't Install steelstorm episode 2"
date: 2011-05-18
forum: Gaming &amp; Leisure
---

### Post by maizuddin35 on 2011-05-18
Hello guys!
I hope there is someone can solve this one.

I just bought steelstorm episode 2 from ubuntu software center, while waiting for everything to get done, suddenly my computer turn off due to the electricity , when I turn back on , and try to install back via ubuntu software center , it said ;

[B]check your internet connection. failed to download package etc...

[/B]after that I try to [B]sudo apt-get update --fix-missing

[/B]then, try to install via terminal , so here is the output :

```
adib@pc35:~$ sudo apt-get install steelstorm-episode2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  steelstorm-episode2-data
The following NEW packages will be installed:
  steelstorm-episode2 steelstorm-episode2-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 654 MB of archives.
After this operation, 666 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  steelstorm-episode2-data steelstorm-episode2
Install these packages without verification [y/N]? y
Err https://private-ppa.launchpad.net/commercial-ppa-uploaders/steel-storm2/ubuntu/ natty/main steelstorm-episode2-data all 2.00.02626-0maverick1
  SSL connection timeout at 115549
Err https://private-ppa.launchpad.net/commercial-ppa-uploaders/steel-storm2/ubuntu/ natty/main steelstorm-episode2 i386 2.00.02626-0maverick1
  SSL connection timeout at 118221
Failed to fetch https://thenameisadib:S52rndlf3X7679bX1vDW@private-ppa.launchpad.net/commercial-ppa-uploaders/steel-storm2/ubuntu/pool/main/s/steelstorm-episode2/steelstorm-episode2-data_2.00.02626-0maverick1_all.deb  SSL connection timeout at 115549
Failed to fetch https://thenameisadib:S52rndlf3X7679bX1vDW@private-ppa.launchpad.net/commercial-ppa-uploaders/steel-storm2/ubuntu/pool/main/s/steelstorm-episode2/steelstorm-episode2_2.00.02626-0maverick1_i386.deb  SSL connection timeout at 118221
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I've been trying and trying but it seems something has gone wrong when the computer suddenly turn off.

---

### Post by motorsep on 2011-05-18
Try sudo dpkg --purge steelstorm-episode2 and then in ~30 min try re-installing it again.

---

### Post by maizuddin35 on 2011-05-18
there is not installed package when i try to do that, thanks for the reply btw.

```
sudo dpkg --purge steelstorm-episode2
[sudo] password for adib: 
dpkg: warning: there's no installed package matching steelstorm-episode2

```

---

### Post by motorsep on 2011-05-18
I reported the issue to Canonical. We shall see what they can come up with.

---

### Post by maizuddin35 on 2011-05-18
I hope they will think of something to deal with , cause I already pay for the game you know . what is the problem exactly?

---

### Post by motorsep on 2011-05-18
I have no idea. All issues with Ubuntu Software Center should be addressed to Canonical. I have no control over it.

---

### Post by maizuddin35 on 2011-05-18
motorsep, are you part of the steelstorm team?

---

### Post by maizuddin35 on 2011-05-18
yes , you are one are part of the team, i see you in indiedb.com :) I hope this problem will be deal with.
i have sent message to your guys mail.

is there any how I can download the game in other operating system such as windows?

---

