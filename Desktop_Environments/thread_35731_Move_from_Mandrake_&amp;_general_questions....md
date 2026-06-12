---
title: "Move from Mandrake &amp; general questions..."
date: 2005-05-20
forum: Desktop Environments
---

### Post by cmo on 2005-05-20
Hi guys,

I've been using Mandrake since 2001, but after running Kububtu under VMWare I'm considering replacing Mandrake with Kubuntu.  But I have a few questions:

1) Has anyone else switched from Mandrake?  Any pros and cons?
2) If I do an expert install of Kubuntu will I be able to use my exisiting /home partition and just replace my / partition with Kubuntu?
3) Is there an option to choose between ext3 and reiser?
4) Generally, is hardware detection as good as Mandrake's?

Any help and info would be appreciated.

Cheers,

cmo

---

### Post by bdmp on 2005-05-20
I switched from mandrake to Kubuntu.  Mandrake looks slick, but kubuntu works better on every front.  Better hardware detection and set up.  The install is easy and straight forward. 
You don't need to do expert install, but it automatically in stalls in ext3 so you will have to change that manually.  Also this faq is awsome. It will tell you how to set up what ever you need [http://ubuntuguide.org/](http://ubuntuguide.org/)

good luck

---

### Post by ymeyer on 2005-05-20
2) If I do an expert install of Kubuntu will I be able to use my exisiting /home partition and just replace my / partition with Kubuntu

I have a Mandriva 2005 on two partitions one for / one for /home with a first user joe.
I have installed Kubuntu on two other partitions for / and /home with the same  user name Joe. 
The Mandriva joe has a user number 501, while the Kubuntu joe was 1000. It was necessary to change the  joe number and joe group numbers to 501 to get RW rights on the two joe partitions both from Mandriva and from Kubuntu.
It is easily done by changing those numbers in /etc/passwd

I am not sure that using the /home from Mandrake as /home for Kubuntu is a good idea. Both distros use different versions of KDE and other programms and you will probably get uncompatibilities between the configuration files. 


4) Generally, is hardware detection as good as Mandrake's?
no problem for my configuration

---

### Post by cmo on 2005-05-20
Thanks for the replies guys.

Another, probably, stupid question:

What's with using 'sudo' for things that require root access?  Isn't it better to have to log in as root to change config files and so on, rather than just using the user's password, as per the way Mandrake works? Or am I stuck in the past??
I assume it must be okay, as Kubuntu's set up that way, but why??

Cheers,

cmo

---

### Post by feeny on 2005-05-20
One major advantage in Kubuntu is apt-get. It never got me into a depedency hell like urpmi did.

---

### Post by xristos on 2005-05-20
[QUOTE=cmo]What's with using 'sudo' for things that require root access?  Isn't it better to have to log in as root to change config files and so on, rather than just using the user's password, as per the way Mandrake works? Or am I stuck in the past??
I assume it must be okay, as Kubuntu's set up that way, but why??[/QUOTE]
Well this is done to protect the new users from "accidentally" harming their computer .

If you are familiar with logging in with root account you can do so from gdm preferences and tick the option "allow root to log in" .

Also from the normal user terminal you can switch to root by typing 

```
sudo -s -H
```

---

