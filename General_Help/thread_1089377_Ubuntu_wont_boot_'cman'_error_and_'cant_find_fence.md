---
title: "Ubuntu wont boot: 'cman' error and 'cant find fence tool'"
date: 2009-03-07
forum: General Help
---

### Post by Admiral Yi on 2009-03-07
Hello,
I have recently rebuilt my computer and I just installed Ubuntu 8.10 last night. I got it to download a load of programs I wanted. After that I shut it down and though I would come back and work on it this morning. That wasn't the first shutdown, I did reboot before I installed anything just to check it worked.

When I started it up this morning, it got just over half way throught the loading screen before it froze and came up with a command line. I got these errors: 

```
Fenced[4896]:Cman_admin_init error 2
dlm_controld[4904]: cman_admin_init error 2
gfs_controld[4904]: cman_admin_init error 2
```

It tried booting three times and the number in the brakets was different every time. After that it comes up with:

```
Fence_tool: Waiting for cman to start
Fence_tool: Waiting for cman to start
Fence_tool: Waiting for cman to start
Ccs[4873]: [ccs   ] Unable to connect to cluster infrastructure after 30 secs

Fence_tool: Waiting for cman to start
Fence_tool: Waiting for cman to start
Fence_tool: Waiting for cman to start
Ccs[4873]: [ccs   ] Unable to connect to cluster infrastructure after 60 secs

```

And so on. Nothing seems to work. I suspect one of my downloads went bad but I have know idea which one. The programs plus all the depndancies came to over 300 files so any one could be the culprit. Should I reinstall?

_EDIT_
After leaving it for 300 seconds it started. One of the programs I seem to have acquired is called cluster management. When I start it, it says: 'the cluster configuration file /etc/cluster/cluster.conf does not exist on this system'. This seems to be the problem. What can I do to remedy this?

---

### Post by TehBleachBottle on 2009-04-16
I am having the same trouble as well. I had just checked for updates and installed them as well as installing a few programs. This had happened to me before when I had after installing programs but I had chalked it up to the fact that I had installed Ubuntu Studio files. I would at least appreciate knowing if I need to reinstall or not. Also I am unable to boot in recovery mode as well.

---

### Post by bushboy on 2009-10-27
I got the same thing when I upgraded to the new 8.10. When I try to use the keyboard or mouse they don't work and I can't type my password in....

---

