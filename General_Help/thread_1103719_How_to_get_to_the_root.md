---
title: "How to get to the root"
date: 2009-03-23
forum: General Help
---

### Post by Trafficflow on 2009-03-23
Can somebody tell me something simple. How do you get to the root? And do you need to be there to make changes?

---

### Post by pbpersson on 2009-03-23
> **Trafficflow said:**
> Can somebody tell me something simple. How do you get to the root? And do you need to be there to make changes?

Your question could mean a few things:

1.  How do I get root privileges on the machine
2.  How do I get to the root directory on the hard drive?

Your last question baffles me.  You do not need to be at the root directory or have root access unless the changes you need to make.....well, you would really never need to make any changes in the root directory.

What exactly do you want to know?  I am confused....  :confused:

---

### Post by iaculallad on 2009-03-23
> **Trafficflow said:**
> Can somebody tell me something simple. How do you get to the root? And do you need to be there to make changes?

You can become a root user by:

```
sudo -i
```

or

```
sudo su
```

And, if you meant going to the root directory:

```
cd /
```

*You need to have an administrative privilege in order to make system changes*

---

### Post by Trafficflow on 2009-03-23
Hello I am new 1 week and learning. Should saw me last week.I have my wireless adapter loaded and no internet. I am wanting to look at config. Do I need to be in the root? I sounds like not.Just learning

---

### Post by iaculallad on 2009-03-23
You don't have to be a root to view your config files. You could just use the command below:

i.e: 

```
cat /etc/fstab
```

Command above will let you view the fstab file from your terminal window.

But you need to have an elevated privilege in order to make changes on your config files.

i.e:

```
gksudo gedit /etc/fstab
```

---

### Post by hyper_ch on 2009-03-23
please have a look at the security section sticky topics about root login.

---

