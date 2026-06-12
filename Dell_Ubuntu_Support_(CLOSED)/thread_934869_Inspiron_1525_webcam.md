---
title: "Inspiron 1525 webcam?"
date: 2008-10-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chummers36 on 2008-10-01
Is it possible to get the web cam to work for the inspiron 1525?

---

### Post by chummers36 on 2008-10-01
I'm running Ubuntu 8.04

---

### Post by siba.s.nayak on 2008-10-01
Hi,
I do have Dell Inspiron 1525 and have installed UBUNTU 8.04. When I installed it, it was asking me for the user Id. At first instance I gave "root" but it denied as the root is reserved user. So I gave "ssnayak" and gave password for it. I just wanted to know, If I can login as user "root" and what is the password for it?

I am asking this querry here as I can not get how to start a new thread?

Please do reply to this thread.

Regards,
S S Nayak

---

### Post by Sand Lee on 2008-10-02
**@chummers36**
I have an Inspiron 1525, w/ Integrated Webcam. It should work without any extra configuring. Try using "Cheese" to test it out.

**@siba.s.nayak**
You cannot log in as the "root" user - it's disabled in Ubuntu. Instead you can use the 'sudo' command in the terminal to access root privileges (the password is ssnayak's password.) [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
And to start a new thread, click on the "New Thread" button above the red forum title. 
In this case it's [COLOR="Red"][SIZE="3"][FONT="Arial"]Threads in Forum : Dell Ubuntu Support[/FONT][/SIZE][/COLOR]

If this answers your question, go to Thread Tools -> Mark as solved.

---

### Post by siba.s.nayak on 2008-10-03
Hello,

I need one more help from the forum. I have taken BSNL EV-DO wire less connection and I am accessing it from Windows XP. But don't know how can I connect to internet from Ubuntu. Can anyone helpme out?

---

### Post by siba.s.nayak on 2008-10-03
Hello Sand Lee,

Thanks a lot. YEs I am doing the thing using sudo command. I didn't know that root user is disabled in ubuntu. Again thanks for you support. For Starting a new thread I clicked on the said buttot but that is not new thread but it is "New Reply".


> **Sand Lee said:**
> **@chummers36**
I have an Inspiron 1525, w/ Integrated Webcam. It should work without any extra configuring. Try using "Cheese" to test it out.

**@siba.s.nayak**
You cannot log in as the "root" user - it's disabled in Ubuntu. Instead you can use the 'sudo' command in the terminal to access root privileges (the password is ssnayak's password.) [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
And to start a new thread, click on the "New Thread" button above the red forum title. 
In this case it's [COLOR="Red"][SIZE="3"][FONT="Arial"]Threads in Forum : Dell Ubuntu Support[/FONT][/SIZE][/COLOR]

If this answers your question, go to Thread Tools -> Mark as solved.

---

### Post by Sand Lee on 2008-10-05
You have to actually leave *this* thread and go to the main category forum to see the "New Thread" button.

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

---

### Post by beno1990 on 2008-10-05
To get some of the drivers for the Inspiron 1525 working you need to install the Hardy backports kernel modules.

This link is the module package for the current kernel version, but make sure you download the right modules for the kernel you have installed.

[http://packages.ubuntu.com/hardy-updates/linux-backports-modules-2.6.24-19-generic]("http://packages.ubuntu.com/hardy-updates/linux-backports-modules-2.6.24-19-generic")

---

### Post by Sand Lee on 2008-10-07
> **beno1990 said:**
> To get some of the drivers for the Inspiron 1525 working you need to install the Hardy backports kernel modules.

This link is the module package for the current kernel version, but make sure you download the right modules for the kernel you have installed.

[http://packages.ubuntu.com/hardy-updates/linux-backports-modules-2.6.24-19-generic]("http://packages.ubuntu.com/hardy-updates/linux-backports-modules-2.6.24-19-generic")
better to download from synaptic/ 
use this apturl link:
[linux-backports-modules-hardy]("apt://linux-backports-modules-hardy")

---

