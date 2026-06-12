---
title: "Error with pbsetup."
date: 2008-08-24
forum: Gaming &amp; Leisure
---

### Post by Gabt on 2008-08-24
Hey, 

So i have this problem with pbsetup.

Let me start from further back, i had big hardware change. Mobo, proc. Ofcourse linux and windows wouldnt boot, i knew that, so i installed a fresh xp, stuck my ubuntu cd in the drive, and restarted, only to be hit with errors: hda:drive not ready for command, during boot from cd. So, i used a windows ubuntu installer thing, it downloaded the installation files.

So... before i changed this hardware, my 32bit ubuntu worked, et worked, pbsetup worked, now this auto installer thing i used, cant remember its name, has installed what i think is a 64 bit version (GCC Vers 4.2.3 (x86_64-linux-gnu)), and THATs what i thinks the problem :(

BUT, ive installed all my other stuff, customized ubuntu and things, and REALLY dont want to have to redo an install either.

Heres the output from the terminal:
```
kev@kev-desktop:~$ '/home/kev/Desktop/pbsetup.run' -e
pbsetup v2.0
Since this is the first time you've run the PunkBuster Setup, we need to check for updates.
Checking for update...Please Wait
Resolving update servers...
Downloading a new global config file...
 **ERROR: Downloading a global config file failed for the following reason:

Couldn't resolve host 'websec2.evenbalance.com'
kev@kev-desktop:~$ 
```

I tried 
```
kev@kev-desktop:~$ '/home/kev/Desktop/pbsetup.run' -add-game=et --add-game-path=/home/kev/.etwolf

```
But it returned the same error.

Anyone got any ideas on why it cant download this file?

Oh, and yes, i did think maybe the server websec2.evenbalance.com was down, but its not.

---

### Post by Gabt on 2008-08-24
Fixed: 
```
sudo -i
echo "208.64.161.186 websec2.evenbalance.com" >> /etc/hosts
```

---

### Post by dbbolton on 2009-06-10
Thanks, this helped me. 

I had to add

```

69.64.64.116 webfile2.evenbalance.com

```

As well.

---

