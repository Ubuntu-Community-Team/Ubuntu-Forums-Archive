---
title: "How do I add a line to sources.list file ?"
date: 2009-05-03
forum: General Help
---

### Post by ericstrom on 2009-05-03
I'm trying to load some software. The add/remove will not add the latest version. The website says before loading the latest version, I have to add the following line to my sources.list file

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

I'm using Jaunty. But new to Linux. How do I add this line ?[FONT="Arial Black"][/FONT]

---

### Post by Titan8990 on 2009-05-03
To add a line to a file: 

```
echo 'deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main' >> /etc/apt/sources.list
```

---

### Post by MaxIBoy on 2009-05-03
You need to run it with "root" (AKA "superuser" AKA "administrator") privileges. This way, some random person couldn't waltz up to your laptop and mess with your system files.


An explanation of UNIX permissions and how to use them:
[http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php](http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php)

The one difference from the tutorial is that in Ubuntu, the root password is unset by default. Instead of using "su," add "sudo" to the beginning of every command that requires root access. This was a design choice by the Ubuntu team, to stop people from running around as root when all they're doing is checking email and such. The idea behind "sudo" is that you only use it to give root access to commands you understand.


I wish you luck with Linux!

---

### Post by Paqman on 2009-05-03
> **ericstrom said:**
> How do I add this line ?[FONT="Arial Black"][/FONT]

Go to System > Admin > Software sources > 3rd party and hit the add button.

---

