---
title: "Is there an easy way to modify the menu of Grub 2 ?"
date: 2009-11-21
forum: Desktop Environments
---

### Post by cstoh on 2009-11-21
Hello experts out there. Is there an easy and convenient way to change the list of options in Grub 2? I have Windows and Ubuntu installed in my Dell Inspiron 545 Desktop PC. Windows is the last option. I would like to change that so that if I don't specify, Windows would be started booted first.

Thanks in advance.

---

### Post by drs305 on 2009-11-21
Take a look at this link. It details how to change the most common settings in GRUB 2, including the default OS:
[GRUB 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")
Look at the 'Menu Default Entry' section.

For Grub legacy there was an excellent GUI app called StartUp-Manager. Parts of it still work with G2, but some parts don't so I generally don't include it in options. It *should* work for selecting the default OS. There is a SUM link in my signature line.

---

### Post by cstoh on 2009-11-23
Thanks a million Drs305. I decided to use the first option, that is, install Startupmanager. Instead of using apt-get install, I looked in my Synaptic Package Manager and found that there was an Startupmanager. I installed it and it became a tool in my admin menu. When I ran it it actually came up with a GUI. For startup sequence, I did not have to remember which sequence. All the available options were selectible from a drop down box. Real cool.
Thanks a million again.

> **drs305 said:**
> Take a look at this link. It details how to change the most common settings in GRUB 2, including the default OS:
[GRUB 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")
Look at the 'Menu Default Entry' section.

For Grub legacy there was an excellent GUI app called StartUp-Manager. Parts of it still work with G2, but some parts don't so I generally don't include it in options. It *should* work for selecting the default OS. There is a SUM link in my signature line.

---

### Post by reeboker on 2009-11-23
> **cstoh said:**
> Hello experts out there. Is there an easy and convenient way to change the list of options in Grub 2? I have Windows and Ubuntu installed in my Dell Inspiron 545 Desktop PC. Windows is the last option. I would like to change that so that if I don't specify, Windows would be started booted first.

Thanks in advance.

More detailed specs. 
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

