---
title: "Ingoring apps in ubuntu update"
date: 2005-03-30
forum: Desktop Environments
---

### Post by teumima on 2005-03-30
Hi

Every time I run apt-get upgrade it gives me the following:

amichai@bzq-179-124-6:~/downloads/Pcsx2$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xlibmesa-gl-dbg: Depends: xlibmesa-gl (= 6.8.2-6) but 6.8.2-5.1 is installed
  xlibmesa-gl-dev: Depends: xlibmesa-gl (= 6.8.2-6) but 6.8.2-5.1 is installed
  xlibmesa-glu-dbg: Depends: xlibmesa-gl (= 6.8.2-6) but 6.8.2-5.1 is installed
  xlibosmesa4: Depends: xlibmesa-gl (= 6.8.2-6) but 6.8.2-5.1 is installed
E: Unmet dependencies. Try using -f.


I don't want to f-use -f as that is forcing it right? I'm scared it will overwrite my ati settings, and that's the last thing I want after finally getting my ati driver to work.

How do I skip/ignore these packages and have my ubuntu upgrade without upgrading xlibmesa.

Thanks

a.t.

---

### Post by lao_V on 2005-03-30
Try locking the version of software you do not want to upgrade. In synaptic there is an option in one of the menus (sorry can't remember where exactly). I'm sure there is an apt-get alternative as well.

Even if you did upgrade it, I'm not sure it will overwrite the conf file will it?

---

### Post by Roptaty on 2005-03-30
No, -f is not a force option... 
From the apt manual page:
 -f, --fix-broken,
              Fix;  attempt  to  correct  a system with broken dependencies in
              place.

---

### Post by teumima on 2005-03-30
[QUOTE=Roptaty]No, -f is not a force option... 
From the apt manual page:
 -f, --fix-broken,
              Fix;  attempt  to  correct  a system with broken dependencies in
              place.[/QUOTE]
 Hey man.

So I assume its safe it wont override my ati driver and replace it with mesa?

Thanx for ur help ;)

---

### Post by teumima on 2005-03-30
It tries to overwrite my ati driver and i dont want that! 

I want mesa to no longer be an option to upgrade

---

### Post by Strider on 2005-03-31
teumima,
Ran into the same problem you are having a few days ago.  It seems you can't completely remove the mesa stuff so you're kinda stuck with it.  I've not looked into actually removing mesa completely.  However, check out this post: [http://ubuntuforums.org/showthread.php?t=22655](http://ubuntuforums.org/showthread.php?t=22655).  I have a work around posted, depending on if you compiled your own ATI/Fglrx drivers.  I have a custom kernel and I compiled the fglrx module.

The last 3-4 times I did an update I had to run this work around.  I ended up creating a shell script to automate the process.  Give it a shot.

---

### Post by teumima on 2005-04-01
Hi

what if i just dont download it?

---

