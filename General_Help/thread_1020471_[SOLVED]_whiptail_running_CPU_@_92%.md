---
title: "[SOLVED] whiptail running CPU @ 92%"
date: 2008-12-24
forum: General Help
---

### Post by gettinoriginal on 2008-12-24
When I run Htop in terminal I get the following:

[ATTACH]97439[/ATTACH]

What is this "whiptail" thats running 92% ??  This seems to be a new problem, as my total CPU usually is around 24 to 26%.

---

### Post by scragar on 2008-12-24
> Whiptail is a "dialog" replacement using newt instead of ncurses. It provides a method of displaying several different types of dialog boxes from shell scripts. This allows a developer of a script to interact with the user in a much friendlier manner.
Sounds like that task is just running out of control, I can't imagine there being much wrong with killing it off.

---

### Post by gettinoriginal on 2008-12-24
Trouble is, there is no process called whiptail running :confused: so I cannot "end process".  When I add the CPU% here, I get 24% !!  When I try to "kill" it in htop, it just comes back.

[ATTACH]97441[/ATTACH]

Somehow it is installed in Synaptic, but is it necessary to the operation of the system ??

---

### Post by scragar on 2008-12-24
It's going to be in use in displaying some sort of message box, judging by it's CPU usage it's just acting up, kill it off:
```
kill 21120
```
If that doesn't work, try forcing it to die(which means it won't do any cleanup, but it will end almost immediatly, even if it's not responding normally)
```
kill -9 21120
```

---

### Post by gettinoriginal on 2008-12-24
Thanks, that works, now running at 12%.  I even rebooted to see if it automatically resumed and it didn't.  I would still like to know exactly why it was running though, what program, application, etc needs it.

---

### Post by scragar on 2008-12-24
There are a few packages that use it, honestly I'd guess GDM was the cause, but that's far from the only cause(and there's no way to check now you've killed it)```
  alsa-utils
  signing-party
  rcconf
  module-assistant
  modconf
  gkdebconf
  ubuntu-minimal
  psfontmgr
  pppoeconf
  pppconfig
  gdm
  friendly-recovery
  defoma
  debian-goodies
  debconf
  alsa-utils
```

---

### Post by gettinoriginal on 2008-12-24
Thanks, i did recently do a sound system changes, so it looks like Alsa put it in, but since my audio is working fine, I guess I will just live with it  :P

---

### Post by jasman_92627 on 2010-07-25
> **scragar said:**
> It's going to be in use in displaying some sort of message box, judging by it's CPU usage it's just acting up, kill it off:
```
kill 21120
```
If that doesn't work, try forcing it to die(which means it won't do any cleanup, but it will end almost immediatly, even if it's not responding normally)
```
kill -9 21120
```


Another user with the same problem ... I tried those kill suggetions and both times terminal reported "No such process". Not to be put off I went into system monitor, processes, active, and was able to kill there. Now the CPU's are under 10%. So my question is this ... where do I execute the kill commands ?  Is that at /root or /ect or at ___ ?

Thanks

---

### Post by mootpoint on 2010-08-02
> **jasman_92627 said:**
> Another user with the same problem ... I tried those kill suggetions and both times terminal reported "No such process". 
Thanks

run ps aux | grep whiptail (where in the directory tree doesn't matter), and note the process number for whiptail. Then sudo kill -9 <thatprocessnumber>. The process number (such as 21120) is assigned by the kernel when the process is started, and will quite rarely be the same twice. 

m00t

---

