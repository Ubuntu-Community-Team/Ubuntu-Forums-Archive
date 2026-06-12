---
title: "Starting and Ending Desktop Environment"
date: 2007-06-27
forum: Desktop Environments
---

### Post by namvijay on 2007-06-27
Hi All,
I am running Ubuntu server 6.06 on one of my spare PC as a server
Pentium 3 1GHz with only 256MB RAM

I have installed ubuntu desktop to use the desktop environment now and then. I mostly use the shell as thats the best way to learn.

I would like to do 3 things.

1. When I reboot the PC the desktop should not load. I know I can use 'startx' commanf to start the desktop. But how do i actually ensure that desktop does not load upon reboot?

2. How to end the desktop environment without rebooting the PC. Is there a way to end desktop?
3. If it is possible to end desktop without reboot. Will it clear from physical memory?

 Thanks and regards

---

### Post by ComplexNumber on 2007-06-27
> **namvijay said:**
> Hi All,
I am running Ubuntu server 6.06 on one of my spare PC as a server
Pentium 3 1GHz with only 256MB RAM

I have installed ubuntu desktop to use the desktop environment now and then. I mostly use the shell as thats the best way to learn.

I would like to do 3 things.

1. When I reboot the PC the desktop should not load. I know I can use 'startx' commanf to start the desktop. But how do i actually ensure that desktop does not load upon reboot?

2. How to end the desktop environment without rebooting the PC. Is there a way to end desktop?
3. If it is possible to end desktop without reboot. Will it clear from physical memory?

 Thanks and regards
when you boot up, it goes through (some of) the runlevels starting various services....eventually ending up on run level 5. thats the GUI mode. 
whilst i'm not entirely certain of the exact procedure to do this, i can point you in the right direction so that you can stop it from ever reaching  runlevel 5. what you need to change will almost certainly be in /etc/init.d directory. you will also notice that there are various other directories in /etc such rc0.d, rc1.d, etc that control exactly what scripts are executed when entering that specific run level.
i don't know how much you know, so [here]("http://en.wikipedia.org/wiki/Runlevel") is a link about run levels.


2) type in 'init 3'. that's what i used to type in in fedora, but i think that ubuntu has a slightly different init system, so there is a small chance that it may be a different command from 'init'.

3) not entirely sure. i don't think it will stay in physical memory.

---

### Post by namvijay on 2007-06-28
Hi,
Thanks for the info. I am relatively new to linux, so dont really understand.

Let me go back home and look through the run levels.

Any one else for suggestion and guidance??

Thanks for your time

---

### Post by mannheim on 2007-06-28
In Ubuntu, you can stop and start the GUI by stopping and starting the login-manager, which is called "gdm": from a terminal, you can do

```

# To stop the gui:
sudo invoke-rc.d gdm stop

# To start the gui:
sudo invoke-rc.d gdm start

```

If you want to prevent the gui from starting when you boot up the machine, you can remove gdm from the list of services that get started. You can do this using the gui itself (seems strange). Go to "System-->Administration-->Services" and uncheck the box for "Graphical Login Manager (gdm)". Then reboot your machine.

---

### Post by namvijay on 2007-06-28
Hi mannheim,
Thanks. Will difinitely try this out tonight.

---

### Post by namvijay on 2007-06-28
Hi All,
YES! Problem solved. Works perfectly for me.
> # To stop the gui:
sudo invoke-rc.d gdm stop

# To start the gui:
sudo invoke-rc.d gdm start

I did disable the GDM from the services and no more GUI starting whenever a rebooting of PC is required.

Thanks

---

