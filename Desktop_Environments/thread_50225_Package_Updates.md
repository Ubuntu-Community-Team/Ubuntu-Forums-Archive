---
title: "Package Updates"
date: 2005-07-19
forum: Desktop Environments
---

### Post by chrisndebb on 2005-07-19
I get an icon on the task bar showing updates available. When I click on it to download the updates, I get an error message telling another package management is already open such as apt-get or aptitude but, I don't have either opened. When I try to run either apt-get or aptitude I get something similar and here it is,

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

If I have a process running, how do I shut it off and how can I get into my package manager such as Synaptic, apt-get, or aptitude?

---

### Post by hydra on 2005-07-19
for synaptics one u can go into *Administration ---> Synaptics package manager*

and apt-get and aptitude can be called from gnome-terminal by the same commands 

*apt-get and aptitude*

check if the system is not updating at the moment...because maybe u have more running processes without even realize it



Or u can also check into *System tools---> Monitor system* to see the current process running

---

### Post by fimbulvetr on 2005-07-19
try doing a sudo

---

### Post by chrisndebb on 2005-07-19
That's just the problem. I can't get into Synaptic. I get an error message telling me that another package manager is running and reality is I don't have anything running.  I can't figure out how to make stop whatever is running. When I try command line apt-get or aptitude, I get the error message listed in my original posting.

---

### Post by hydra on 2005-07-19
*System tools---> Monitor system* seeeeeee if synaptics is runninggg


or just ctrl+alt+back

---

### Post by hapibooda on 2005-07-19
You may have programs running on more than 1 desktop.

The default installation gives you 4 desktops.  Look in the lower right corner and click on each square (desktop) and see if you have a program running on a desktop other that the one you are currently viewing.

---

### Post by mad_scientist03 on 2005-07-19
Sometimes, if apt-get closes abruptly, it will leave a lock file in place that makes your system think someone is using the update system when it's not in fact being used. I'm much more familiar with the apt-get port to Fedora, so I wouldn't know where to look for such lock files in Ubuntu, but hopefully it's a start.

---

### Post by DancingSun on 2005-07-19
Good 'ol windows method....restart.

---

