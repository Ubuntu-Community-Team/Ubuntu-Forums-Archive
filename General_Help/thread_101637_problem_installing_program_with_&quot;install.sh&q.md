---
title: "problem installing program with &quot;install.sh&quot;"
date: 2005-12-10
forum: General Help
---

### Post by timsch75 on 2005-12-10
I'm trying to install fluxstyles, and I'm directed to run the install.sh file, but am returned the error below.  I've done this plenty of times in slackware.  Why the error in ubuntu?


[email]tim@ubuntu:~/.flux[/email]box/fluxStyle$ ls
fluxStyle  images  install.sh  mods  README

[email]tim@ubuntu:~/.flux[/email]box/fluxStyle$ sudo install.sh 
sudo: install.sh: command not found
[email]tim@ubuntu:~/.flux[/email]box/fluxStyle$ sudo ./install.sh
sudo: ./install.sh: command not found
[email]tim@ubuntu:~/.flux[/email]box/fluxStyle$

---

### Post by tukuyomi on 2005-12-10
Try this:  ```
cd */path/to/your/install*
sh ./install.sh
``` :)

---

### Post by Adrian on 2005-12-10
[QUOTE=timsch75]I'm trying to install fluxstyles, and I'm directed to run the install.sh file, but am returned the error below.  I've done this plenty of times in slackware.  Why the error in ubuntu?


[email]tim@ubuntu:~/.flux[/email]box/fluxStyle$ ls
fluxStyle  images  install.sh  mods  README

[email]tim@ubuntu:~/.flux[/email]box/fluxStyle$ sudo install.sh 
sudo: install.sh: command not found
[email]tim@ubuntu:~/.flux[/email]box/fluxStyle$ sudo ./install.sh
sudo: ./install.sh: command not found
[email]tim@ubuntu:~/.flux[/email]box/fluxStyle$[/QUOTE]

Make sure that the install script is executable

```
chmod a+x install.sh

```

---

### Post by SirKillalot on 2005-12-10
Make sure you can execute programs on that partition (/etc/fstab)

---

### Post by timsch75 on 2005-12-10
Thanks all,   "sh" did it.  I had made it executable (it wasn't, for some reason).  I'd swear I never had to do that before in Slack.  Maybe I'm just losing it....

---

### Post by taurus on 2005-12-10
[QUOTE=timsch75]Thanks all,   "sh" did it.  I had made it executable (it wasn't, for some reason).  I'd swear I never had to do that before in Slack.  Maybe I'm just losing it....[/QUOTE]
I don't think so...  I have Slackware running on one of my machines and after downloading, you NEED to change the permission if you want to execute it since the default permissions are read & write only!!!

---

### Post by timsch75 on 2005-12-10
I meant I didn't recall having to use the "sh" command, but on that note I rarely if ever had to change the permissions one one of those either on other programs configured from source

---

### Post by taurus on 2005-12-10
No, you don't have to include the "sh" in front of whatever you want to run.  So, "./install.sh" should be just fine...  However, try not to confuse between an executable file (to extract) and build from source!!!  You don't have to change anything if you download a source and build it from it...  In other words, you would run something like

tar xvjf <filename>.tar.bz2
-or-
tar xvzf <filename>.tar.gz
cd <filename> (newly created directory)
./configure
make
make install

---

