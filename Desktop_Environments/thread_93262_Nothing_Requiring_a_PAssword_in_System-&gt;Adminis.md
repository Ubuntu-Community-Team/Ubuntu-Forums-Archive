---
title: "Nothing Requiring a PAssword in System-&gt;Administration Works"
date: 2005-11-21
forum: Desktop Environments
---

### Post by kilovh on 2005-11-21
This problem has been going on since yesterday, when I installed Ubuntu.

Whenever I try to run a program under System->Administration, such as Synaptic, a box pops up in which I must enter my password. If I enter the root password, it says its the wrong one. If I enter my user password, the dialogue dissapears and nothing happens. Its driving me insane, because I'm itching to get into those programs, particularly the package manager.

I remember that following some advice from some page I found on Google I got Synaptic to work yesterday, but it no longer works and I cannot remember how to get it to run.

Thanks,

Kilovh

---

### Post by angkor on 2005-11-21
What happens if you do:

sudo synaptic

in a terminal with your userpasswd?

---

### Post by kilovh on 2005-11-21
I get the following message:

(synaptic:7798): Gtk-WARNING **: cannot open display:

EDIT: Sorry, that's what happens if I type that command as root user. If I do it as my regular user, there is no error but once again nothing happens.

---

### Post by 23meg on 2005-11-21
Did you by any chance delete your default hosts? Please post the contents of your /etc/hosts file.

---

### Post by kilovh on 2005-11-21
The entire file is:

127.0.0.1 ubuntu.localdomain ubuntu


Ubuntu being my computer name...

---

### Post by 23meg on 2005-11-21
Make the file look like this, save it, reboot, and see if anything changes. 
```
127.0.0.1 localhost.localdomain localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by ace2005 on 2005-11-21
Ok well since you can't run any graphical programs as root we'll have to use command line

Get into root the way you did before and type this

> /etc/sudoers

This will bring up the sudo users information file

> kilovh       ALL = NOPASSWD: ALL

Change "kilovh" to whatever you're username is on that computer, from now on you should be able to run any app using sudo ...

So run "sudo synaptic" and enjoy

I get that error too

> root@Linux:/home/ace# konqueror
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

konqueror: cannot connect to X server :0.0
root@Linux:/home/ace#


---

### Post by kilovh on 2005-11-21
Thanks a ton Ace -- problem solved.

---

