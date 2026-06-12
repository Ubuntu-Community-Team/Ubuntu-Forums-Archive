---
title: "Choosing what to install by default"
date: 2006-02-23
forum: Desktop Environments
---

### Post by scav on 2006-02-23
Hi,

I want to customize the "default" installation of ubuntu, like I want ndiswrapper, krb5 .deb packages etc. to be installed by default, does anyone know what file, or what directory i need to configure to get it to install more packages, than the ones that are default with the ubuntu cd?

Many Greetings

---

### Post by lamego on 2006-02-23
My approach to do a custom install is:
Install the base system by booting the install cd with the "server" option.
Then after having the base system installed I just use apt-get to install the other things I need.

---

### Post by scav on 2006-02-24
Well, yeah I know, but my goal, is that all packages I want gets installed under the installation of the system!

We have 250 laptops at my work, and we are looking for other operating systems than MS to roll out, therefore a solution were everything were ready right after the install, would be great.

---

### Post by nanotube on 2006-02-24
well, some of the packages may not even be available on the ubuntu install cd.
if you want to automate the install of these extra packages, just make a list of the packages you want, and run a giant command line with 
```
sudo apt-get install package1 package2 ... packageN
```
after the install.
if you want to avoid downloading all these from the repositories every time, you might consider installing package "apt-proxy" on one of your machines, which would cache all these packages you want to install the first time, and then other machines can pull from it, rather than downloading from the net.

---

### Post by scav on 2006-02-24
yes, the trick will be to automate it all, maybe through kickstart.

I want to be able to just insert a cd, choose a computer name, and the name of the user who will be using in it...

It will authenticate to a Active Directory server.. Ive got that working easily, but it would be to much work doing it manually on 250 pc's

---

### Post by lamego on 2006-02-24
If you have good LAN enviroment I would do it from the network.
After installing with the "server" option you would only need to run a script which would take care of all the rest of the processs (installing the required, packages, custom configuration, etc).
This would give you the extra flexibility of changing the install process on the server side to include whatever packages or customizations you decided.
Anyway this can also be achieved with CDs, just use the base ubuntu CD for the install and put the script and the other packagtes on a differente CD that you would use after the "server" install.
Please note that I am talking about semi-automated, someone would need to write a single command after the base install "which should not take more than a few minutes".

I am familiar with this kind of process for big scale deployment (not really with linux) and it does work.

---

### Post by nanotube on 2006-02-25
hey
might also want to read through this page:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by aysiu on 2006-02-25
If these laptops are identical (same hardware, same specs), you may want to look into PartImage.

You can set up one laptop exactly the way you want, copy that partition to an external hard drive and then copy it to the other 250 laptops.

There may be a ghost-ing program out there, too, somewhere...

---

### Post by ihateemo on 2006-02-25
Yeah, from what I can tell (s)he's trying to create a CD image than can just be inserted and installed without having to do anything else.

---

