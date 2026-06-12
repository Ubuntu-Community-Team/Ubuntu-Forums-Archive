---
title: "hello need some help with ati card"
date: 2011-06-07
forum: Colorado Team - US
---

### Post by delpgdn on 2011-06-07
I'm from the springs area and just joined loco. I started with 8.04 now at 10.04 In all this time i still can't get a radeon 9000 to work. In 10.04 i'm using the open source driver and no work as usual.My xorg log says x is loading before kms.im not to clear on the command to fix the problem


The driver is installed as well as control panel and compiz. thank you p.s.warning i have other problems.

---

### Post by joey on 2011-06-07
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Blasphemist on 2011-06-08
Welcome! I'm also in the springs. The link posted is the page for the open source ati driver and that should be what you run unless you are having a speed issue. It sounds like you have other issues too so lets get some background. One of my laptops has ati too and it is my test/messin laptop so maybe that will help.

Your other problems may not be involved but just in case, and so we can solve them too, please start with boot issues if you have any and describe your issues with as much detail as possible. I'll ask for specific detail based on the issues if I don't see it in your answer.

Have you ever installed the proprietary fglrx driver? If you have there is sometimes a process needed to fully remove before you can get the open source driver to work.

Are you on 10.04 because it is the LTS or for some other reason? I'm not going to work on you to upgrade to natty but I can help if you want to. I've been on it for months.

---

### Post by Blasphemist on 2011-06-17
> **Blasphemist said:**
> Welcome! I'm also in the springs. The link posted is the page for the open source ati driver and that should be what you run unless you are having a speed issue. It sounds like you have other issues too so lets get some background. One of my laptops has ati too and it is my test/messin laptop so maybe that will help.

Your other problems may not be involved but just in case, and so we can solve them too, please start with boot issues if you have any and describe your issues with as much detail as possible. I'll ask for specific detail based on the issues if I don't see it in your answer.

Have you ever installed the proprietary fglrx driver? If you have there is sometimes a process needed to fully remove before you can get the open source driver to work.

Are you on 10.04 because it is the LTS or for some other reason? I'm not going to work on you to upgrade to natty but I can help if you want to. I've been on it for months.

I left something out of the instructions in my personal message back to you. You may not need this but just in case, to edit grub:
```
cd /etc/default
gksudo gedit grub
```
Save your changes and then run:
```
update-grub
```

---

