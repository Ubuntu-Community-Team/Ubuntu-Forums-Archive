---
title: "Scorched 3D"
date: 2006-10-01
forum: Desktop Environments
---

### Post by spyker3292 on 2006-10-01
When I try to install Scorched 3D I type

sudo apt-get install scorched3d

and it can't find the package
same thing with about any onther thing I try to install

---

### Post by meng on 2006-10-01
Please post the output of:
cat /etc/apt/sources.list

---

### Post by spyker3292 on 2006-10-01
> **meng said:**
> Please post the output of:
cat /etc/apt/sources.list

? (sorry I'm kinda new)

---

### Post by kewldude606 on 2006-10-01
Go to Applications-->Accesories-->terminal and type in cat/etc/apt/sources.list, select everything that appears with your mouse, right click and pick copy, then post it here by making a new post and pressing control and v at the same time.

---

### Post by meng on 2006-10-01
"Post the output of a command" means you should execute the command in terminal and copy and paste the result (output) in a post on this forum.

I suspect your problem is that you haven't enabled extra repositories (you need to enable universe to install scorched3d, for example). The command will tell me what repositories you do have enabled.

---

### Post by spyker3292 on 2006-10-01
Heres what happens

sudo apt-get install scorched3d
Reading Package List... Done
Building dependency tree... Done
E: COuldn't find package scorched3d

---

### Post by meng on 2006-10-01
Wrong command. The command I need you to run, to identify the problem, is:
cat /etc/apt/sources.list
Please read carefully!

---

### Post by spyker3292 on 2006-10-01
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by spyker3292 on 2006-10-01
> **meng said:**
> Wrong command. The command I need you to run, to identify the problem, is:
cat /etc/apt/sources.list
Please read carefully!

sorry but now I posted it. Will this make it so apt-get always works?

---

### Post by meng on 2006-10-01
Okay, my suspicions are correct. Here's how to fix it:

1) From terminal, type:
gksudo gedit /etc/apt.sources.list

2) In the text editor that comes up, remove the leading #'s from all lines beginning with "# deb" (there are six such lines). This will enable universe and multiverse repositories, from which you can download/install the programs you are after.

3) Save and exit the text editor

4) Run in terminal:
sudo apt-get update

5) Run in terminal:
sudo apt-get install scorched3d

---

### Post by spyker3292 on 2006-10-01
great it worked! this will help a lot.

---

