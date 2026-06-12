---
title: "Killing an X Server"
date: 2009-06-21
forum: General Help
---

### Post by beastrace91 on 2009-06-21
I am using multiple X servers to run my different games as they tend to run at a slightly higher frame rate (especially in the case of wine/cedega games) I have it setup so that the new X server terminates after the program closes but on the occasion that my game crashes I have an extra X server floating around until I reboot. How I can kill off just my extra X servers (so all those other than my primary one)

Thanks,
~Jeff

---

### Post by ratcheer on 2009-06-21
I just had to do this, myself, about 10 minutes ago. I was reinstalling my video driver and an old X server was still running. I don't know the proper way to do it, but this worked:

ps -ef | grep "/usr/bin/X"   -- (This will return the PID of the X process)

sudo kill -9 nnnn    -- (where nnnn is the PID from above)

Tim

---

### Post by beastrace91 on 2009-06-21
Hrm, when I run the kill commands it keeps killing my terminal window and not the other X server

```
jeff@lintop:~$ ps -ef | grep "/usr/bin/X" --
jeff      7799  7771  0 19:21 pts/1    00:00:00 grep /usr/bin/X --

```

I used the second number, so like ```
sudo kill -9 7771
```

And the other X server is still there.

Suggestions?
~Jeff

---

### Post by ratcheer on 2009-06-21
No, the 7799 is the PID of the X process. 7771 is its parent.

But wait, that is not the X server process, at all. That only found your grep command process.

Tim

---

### Post by ratcheer on 2009-06-21
I promise this is not what I found when I was trying to install my video driver, but here is what I get now, while I am up in full graphics mode:

```

root      2630  2626  2 18:54 tty7     00:01:11 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
tim       5543  5525  0 19:39 pts/0    00:00:00 grep X

```

Tim

---

### Post by beastrace91 on 2009-06-22
huh, so anyone know how I can go about killing an extra X server that is hanging around?

~Jeff

---

### Post by Entropy_Sam on 2009-06-22
When installing the latest nVidia drivers, I killed ALL x-servers by switching to tty1 and typing ```
sudo /etc/init.d/gdm stop
``` then restarted it with ```
sudo /etc/init.d/gdm restart
```
 
I guess you can swap "gdm" with "kdm" if you're using Kubuntu.
 
Lacks any finesse of course, especially if you don't want to close any other apps open on another X server, but it certainly works...

---

### Post by ratcheer on 2009-06-22
Sam, you see, that is what didn't work for me. I was reinstalling my nVidia driver after the kernel update. I did the "sudo /etc/init.d/gdm stop" and it responded, "OK". Then I tried the driver install. It failed because an X-server was still running. Then, I found and killed the X process as I said in my post, above. Then installing the driver ran just fine.

This is all very confusing.

Tim

---

### Post by beastrace91 on 2009-06-22
Not quite, I understand what both of you are saying. But none of it is the answer to my question.

```
sudo /etc/init.d/gdm stop
``` Stops the Gnome display manager... (and X) but as you also mentioned this is not what I am looking for because I only want to stop the extra X servers I have running.

As for the kill command, I looked it up and as I thought it is a command to stop a certain process from running not the X server (which does not have a process ID from what I can tell) Any other suggestions?

~Jeff

---

