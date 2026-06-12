---
title: "Trying to install bluefish"
date: 2006-08-12
forum: Desktop Environments
---

### Post by Xevor on 2006-08-12
I got tired of Windows XP so I installed ubuntu again and now I want to keep it and learn more about it :)

I am trying to do everything to install bluefish but it just doesn't works. According to the site typing "apt-get install bluefish" should work but it doesn't because there is no bluefish in the packages.

Finally after install all kind of packages ./configure works but I don't know what to do next.

It says typ ./configure and after that make but after the ./configure process is finished I tried to type "make" and "make install" but the only thing I got was this:
"bash: make: command not found"

So how do I have to install it?

---

### Post by baldy1324 on 2006-08-12
ok the first way they say is the good way to use b/c this uses binary (dont have to compile-ready to install) and are built in ubuntu. what you can do is open synaptic package manger in System-->Administration-->Synaptic Package Manger at the top of the screen. Then go to Settings-->Repositories and the check the item that says universe. you can now close synaptic and run apt-get install bluefish. what we did is enabled the universe repository that ubuntu dosen't officialy support. what the ./configure, make, make install is download the package's source code and compiling it to make a binary.

that didn't work b/c you have to install the build-essential package which installs the programs that allow you to compile programs from source. you can do this if you run```
apt-get install build-essential
```

also try to search the internet for how to use APT this will teach you how to upgrade,install,remove, and do all kinds of stuff having to do with packages (precompiled software).

hope this help

---

### Post by maniacmusician on 2006-08-12
yup that's all correct. i'm just repost to emphasize something baldy said; unless you have no choice, compiling it yourself is usually an unnecessary hassle. Advantages/Disadvantages:

apt-get/Synaptic:
Easy to install
Works because the packages are built for Ubuntu

Compiling:
You can get newer, cutting edge versions (but unless it's an amazing feature that you need right away, you can also just wait until the package in the repos gets updated.)


You just have to weigh it out. When you're just starting out with linux, synaptic is definitely easier. But eventually, as you get more oriented with Terminal and how to use commands, you will want to try to compile things too. It's a useful skill to have.

edit: here's a guide on how install things in Ubuntu. this link brings you specifically to the compiling from source part, but you can scroll up and down to view the entire guide. [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

