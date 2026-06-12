---
title: "firefox shutting down"
date: 2009-01-21
forum: General Help
---

### Post by miroslav_karpis on 2009-01-21
Hi,
please can you help me with this?

I have installed and saved configuration for my NVIDIA graphic. I'm using twin display (2 displays). 

The problem is that my firefox just randomly shuts-down. I was reading that it might be because of Flash?

Yesterday I was not able to save the config file and the firefox was working ok,....

---

### Post by miroslav_karpis on 2009-01-27
please...any tips?...I have still the problem :(. WHen I browse some pages no problem, but when I switch to some other..firefox just comes down...

---

### Post by Captain Giraffe on 2009-01-27
Im also on NVIDIA graphics, been experiencing this problem for a few days.
 Sometime FF just hangs, or randomly shuts down. Extremely annoying.  How would one go about and troubleshoot this? Cant seem to find anything in the regular logs.

---

### Post by adamlau on 2009-01-27
Try running Firefox in safe mode:

```
firefox -safe-mode
```

---

### Post by miroslav_karpis on 2009-01-27
I gave it a try,..but this was the reply:

**Aborted**

---

### Post by danduq on 2009-02-04
I too am getting this.

I have completely removed FF and my profile and installed from scratch using UbuntuZilla.

Running through strace I got this;
```
14:54:02 wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 3513
14:54:02 chdir("/home/dan")             = 0
14:54:02 clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e38908) = 3514
14:54:02 wait4(-1, Segmentation fault
[{WIFEXITED(s) && WEXITSTATUS(s) == 139}], 0, NULL) = 3514
14:54:18 --- SIGCHLD (Child exited) @ 0 (0) ---
14:54:18 exit_group(139)                = ?
Process 3502 detached
```

Any ideas? It's almost unusable.  :(

---

### Post by miroslav_karpis on 2009-02-19
PLEASEEEEEE!!!!!!!!!!!

This is the most annoying problem - how can I solve this? Even after upgrading tu firefox 3 - the same problem....
and I'm just getting more and more angry :popcorn:

or should I try some other browser?

---

### Post by miroslav_karpis on 2009-02-19
so I tried with Opera - and it is the same...
it is SOOOOOO EXTREMELY ANNOYING!!!!!

Only think I know that I can not work under these conditions....should I reinstall the whole mr. Ubuntu, Or?....

---

### Post by miroslav_karpis on 2009-02-20
nothing?.....then I guess I just have to change to other linux version - maybe suse?......
+ today (after upgrade) stopped to work my sound - perfect!!!!!

---

### Post by nanotube on 2009-02-24
that's a hard one... try asking a question on launchpad. [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by danduq on 2009-03-09
For info, I completely removed Firefox and Ubuntuzilla and my profile and re-installed from scratch and created a new profile.

This seems to (mostly) have fixed it, but I have noticed one thing that quite frequently just shuts down my FF with no warning or error - the Admin interface of a Zeus Load Balancer.

Now, I think this is because of the Flash applet that runs in the top corner, but I haven't come across any other Flash content that causes my browser to collapse.

For the time being, I'm using Opera to administer my load-balancer, and Firefox seems to have been fine since.

---

### Post by miroslav_karpis on 2009-05-07
good news - 9.04 solved the problem :guitar:

thank you guys...

---

