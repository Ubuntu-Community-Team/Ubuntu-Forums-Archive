---
title: "Some Upstart help"
date: 2009-04-23
forum: General Help
---

### Post by harisund on 2009-04-23
Sorry guys .. I think I am kind of real late to the party. 

I understand the old init system has been replaced, and from the looks of it I shouldn't be using my old tools like update-rc.d and whatever. 

So here are some related questions I have - 

How do I add or delete services that I want starting up at boot time? 
How do I get rid of all the ttys that are running in the background? 

For example, I don't want to see gdm get started every single time I reboot. I can do /etc/init.d/gdm stop at the moment, but I want this service to not start at all. Any suggestions?

---

### Post by celthunder on 2009-04-23
look at /etc/inittab and you can set your tty's and startup mode (3 i believe is your inteded startup mode 5 is the default).

---

### Post by harisund on 2009-04-23
There's no /etc/inittab in either my Ubuntu 8.10 installation nor my 9.04 installation (both 32 bit, VirtualBox guests on a Windows XP 32 bit host) 

This is driving me crazy!

---

### Post by kukibird1 on 2009-04-23
If you look in /etc/event.d there are files tty6 to tty1. You can comment out the start lines in the ones you don't want running. I only use tty1 and tty2.

---

### Post by harisund on 2009-04-23
Ah that worked. Neat. 

Now how do I stop GDM from starting every time I boot? I don't want to manually do /etc/init.d/gdm stop every single time :(

---

### Post by kukibird1 on 2009-04-23
> **harisund said:**
> Ah that worked. Neat. 

Now how do I stop GDM from starting every time I boot? I don't want to manually do /etc/init.d/gdm stop every single time :(

It's a graphical login. You can turn it off and login from the console and run startx to get to your desktop. 

System > Administration > Services will let you start and start a few common services. I use a commandline program called sysv-rc-conf to list them all. Please be careful about this so as not to turn off anything required.

---

