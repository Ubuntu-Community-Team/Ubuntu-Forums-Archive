---
title: "auto login from console"
date: 2005-12-25
forum: Desktop Environments
---

### Post by pataphysician on 2005-12-25
i'm running a headless file-server to share files on my lan in my apartment. it's also running apache to host little sig file scripts and some other random things. i don't have any window-system installed in here, it just boots to the console and does its job. my problem is that the machine won't do or respond to anything unless i log into it. so everytime the power goes out long enough for the ups to give up, i have to drag a monitor and keyboard over to it just to log in. i know you can set a default user to login after xx seconds in gnome -- is there anyway to do this via the console?

---

### Post by pharcyde on 2005-12-25
What services/daemons do you need to have running on your system?  It seems to me that if you want these services running at all times then you should have them start up using your init.d.  I may be wrong but it believe you may be having certain programs only load when a user logs in.  If you want a specific maintenance task to run periodically use a cron job.  If you have questions about this or if I'm just being ignorant to your problem PM me and maybe I can help.

---

### Post by sciurus on 2005-12-25
The easy solution is to install ssh so that you can remotely login. Like pharcyde, I wonder why whatever services you're running aren't automatically starting. For instance, I'm running a headless box with Samba, and the default install set it up to start automatically. Have you messed with your runlevels?

---

### Post by pataphysician on 2005-12-25
i have samba, ssh and apache running, but none of them work until i log in. and, uh, i'm really sorry about this, but i've never even heard the term "run level" before.

---

### Post by sciurus on 2005-12-26
You can read about runlevels at [wikipedia.]("http://en.wikipedia.org/wiki/Runlevel"). Basically, each one specifies a set of scripts to run. The actual scripts live in **/etc/init.d**. Each runlevel has a folder **/etc/rc*#*.d** filled with symbolic links to the scripts. For example, when you reboot your computer, what you are really doing is switching to runlevel 6, which has a link to **/etc/init.d/reboot**.

First, make sure you have the proper scripts for your services by entering *ls /etc/init.d* in a terminal. Next enter *runlevel* to verify that you are at runlevel 2, Ubuntu's default. Then run *ls -l /etc/rc2.d* to see what services are set to start at that runlevel. For instance, for samba you should see **S20samba -> ../init.d/samba**. If you don't see these, you can create the links to them yourself. For example, *cd /etc/rc2.d/* followed by *sudo ln -s ../init.d/ssh S20ssh* should set up ssh to start automatically at runlevel 2.

---

