---
title: "root password"
date: 2006-03-12
forum: Desktop Environments
---

### Post by stevken on 2006-03-12
Hi

Just installed Ubuntu on VMWare (first look at Linux) and tried to install VMtools with no success. I am told that I need to use the su -- root command to install it via a terminal but I dont know the root password and I dont recall setting it. 

Can anyone advise?

TIA

Stevie

---

### Post by Wolki on 2006-03-12
Ubuntu has the root password disabled by default. More info here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You can use "sudo command" to run a certain command with root powers, or use "sudo -s" to get acces to a root shell that basically works like "su" does on other distros.

---

### Post by piglet_74 on 2006-03-12
From what I've seen here it's recommended to run everything via sudo or I think gksudo maybe gksu for gui stuff.  If you look though there are ways to change the root passwd to something you know.

---

### Post by stevken on 2006-03-12
OK here is what I tried

bin  doc  etc  FILES  INSTALL  installer  lib  vmware-install.pl
sk1@ununtu1:~/Desktop/test/vmware-tools-distrib$ sudo vmware-install.pl
sudo: vmware-install.pl: command not found


Obviously I am doing something wrong but what is it?

---

### Post by Stormbringer on 2006-03-12
Try it that way:

sk1@ununtu1:~/Desktop/test/vmware-tools-distrib$ sudo **./**vmware-install.pl

or, if it it still doesn't work:

sk1@ununtu1:~/Desktop/test/vmware-tools-distrib$ sudo **sh ./**vmware-install.pl

Cheers,
Storm.

---

### Post by stevken on 2006-03-12
That certainly went further - thanks for that but now I have this 

What is the location of the "make" program on your machine?

Any ideas?

cheers

---

### Post by Stormbringer on 2006-03-12
In a terminal type:

# which make

Should give you an output like:

/usr/bin/make

If it doesn't locate the file, then you're missing the required packages needed to compile sources.

# sudo apt-get install build-essential

This installs all the files you need.

Cheers,
Storm

---

### Post by stevken on 2006-03-12
Storm thanks for all your help - it worked a treat.

I suppose this is easy stuff but at the moment you are a genius in my eyes:) 

Watch for my next queries for I have many.

---

### Post by Stormbringer on 2006-03-12
> Storm thanks for all your help - it worked a treat.

No problem - this community is meant to help each other.

> I suppose this is easy stuff but at the moment you are a genius in my eyes

Actually it is the easy stuff.

> Watch for my next queries for I have many.

Will do.

---

