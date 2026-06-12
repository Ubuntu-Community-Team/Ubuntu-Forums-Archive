---
title: "Managing memory, processes, daemons"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Kensi on 2005-10-28
Coming from a windows background, I am used to running msconfig to see what programs are on startup, disabling ones I don't want etc. I am also used to accessing services.msc and disabling processes that I have no need for, even if it is temporarly to improve my memory usage.

I want to be able to have similar control in Ubuntu, I understand services are called daemons. Is there software that gives me full access and control over the daemons and programs starting up? Also, If I would like to have a daemon on automatic startup that isn't there, where can I do this? Or is this all done through editing files? Even if so, I would much appreciate some information, even a link to a guide, which could help me.

As an example, the beagle daemon I may or may not want starting up all the time, but I am lost as to how I can have control over things like this. Also, there is that update-notifier which I would rather not have running, but again - no ideas how I can remove it.

Thanks!

---

### Post by Sendervictorius on 2005-10-28
This is a big subject, not to be answered in a glib reply. You need to understand about runlevel and a whle lot of things. Maybe others can post links to web pages that can explain things.

However - the short answer, take a look at /etc/init.d

In there you will see all the startup scripts created when the various packages  were instlled on your system. 

The actual execution of these packages when you normally boot (into runlevel 5) is controlled by the presence of a symbolic link in a directory called /etc/rc5.d

Take a look in there wit "ls -l" , and you will see the symbolic links back into the init.d directory.

You control the startup by creating or deleting the links in the rc5.d directory.

There are various gui packages around that will let you control this rather than doing the command line thing. Maybe others can recommend one.

---

### Post by psychicdragon on 2005-10-28
If you have the extra repositories enabled, you can **sudo apt-get install bum** (boot up manager). You have to run this as root.

It shows a list of all the init scripts and a short description of what they do. You can uncheck the ones you don't want sarting up.

---

### Post by kashms on 2005-10-28
There is boot-up-manager (BUM), a gui for controlling services, which is quite good. I should be available through synaptic.

---

