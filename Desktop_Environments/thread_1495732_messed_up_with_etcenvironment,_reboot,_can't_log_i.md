---
title: "messed up with /etc/environment, reboot, can't log in"
date: 2010-05-28
forum: Desktop Environments
---

### Post by adellalin on 2010-05-28
I have tried to add some system variables on my ubuntu 9.04. So I edited /etc/environment like this:

export JAVA_HOME=/usr/local/java
expott GRAILS_HOME=/home/adella/grails
PATH="/usr/bin:..."
export PATH=$PATH:$JAVA_HOME:$GRAILS_HOME/bin

But it didn't work, didn't pick grails on the path. So I figure a reboot may help. It turned out to be a big mistake. I can't even log in, I think it might be this faulty /etc/environment messed up the shell. 

I tried to repair with CD but it didn't find there is anything:( wrong. 

Please help me! What do I do to fix it?

THanks

---

### Post by efflandt on 2010-05-29
Did you really spell it "expott"?  You should not change the whole system environment for something in your home directory, since that path may not have permission for other users. Did you actually try to put those "commands" in /etc/environment (it is not a script)?

From a live CD, mount your system and using sudu nano (or gksu gedit) edit the etc/environment on that system back like it was.  Mine is:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

You should edit your **~/.profile** instead, which is a script that runs when you login.  It is not necessary to "export" from there, just set the variables, since that will set it in your login shell and any sub-shells:

JAVA_HOME=/usr/local/java
GRAILS_HOME=/home/adella/grails
PATH=$PATH:$JAVA_HOME:$GRAILS_HOME/bin

---

