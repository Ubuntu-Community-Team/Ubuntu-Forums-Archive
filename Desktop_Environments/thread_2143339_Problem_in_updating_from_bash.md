---
title: "Problem in updating from bash"
date: 2013-05-08
forum: Desktop Environments
---

### Post by mahmoud moosa on 2013-05-08
Hello everybody,

After installing ubuntu (64-bit) version, i want to update from bash shell.
once i execute the command, i receive error as shown in the screen shot.

Any idea please ?

Thank you for any help.









[ATTACH=CONFIG]242343[/ATTACH]

---

### Post by papibe on 2013-05-08
Hi mahmoud moosa.

It looks like the 'Update Manger', also called 'Software Upgrade' is running in the background also updating the sources. Since just one app at a time can access the sources files, you are temporally lock out.

Wait a couple of minutes and the Update Manger will appear. If it doesn't (no upgrades available), you could try again from the command line.

Let us know how it goes.
Regards.

---

### Post by Bashing-om on 2013-05-08
mahmoud moosa; Hi !

That error is generally indicative that more than one instance of a package manager is open. As in the Software Center or synaptic or another instance of dpkg is running when you attempt to run "sudo apt-get".

Insure all applications are closed out, re-boot and see if that error then occurs ...
[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by mahmoud moosa on 2013-05-08
> **papibe said:**
> Hi mahmoud moosa.

It looks like the 'Update Manger', also called 'Software Upgrade' is running in the background also updating the sources. Since just one app at a time can access the sources files, you are temporally lock out.

Wait a couple of minutes and the Update Manger will appear. If it doesn't (no upgrades available), you could try again from the command line.

Let us know how it goes.
Regards.

Hello my friend,

I will give it time.
I will update you the results.

Thank you for your help.

---

### Post by mahmoud moosa on 2013-05-08
> **Bashing-om said:**
> mahmoud moosa; Hi !

That error is generally indicative that more than one instance of a package manager is open. As in the Software Center or synaptic or another instance of dpkg is running when you attempt to run "sudo apt-get".

Insure all applications are closed out, re-boot and see if that error then occurs ...[INDENT=3]
just try'n to help

[/INDENT]


Hello my friend,

Once loged in ubuntu, directly i opened bash and typed the update command without opening any other application.
I did what you advised, but still the same error.

Thank you for your help.

---

### Post by Bashing-om on 2013-05-08
mahmoud moosa;
Do not understand how that could be // that error reflects another instance of a package manager open at the same time.
Delving deeper, lets see the out put - placed between the threads code (#) tag - of terminal code:
```
sudo ls -la /var/lib/apt/lists/lock
``` should be file size 0 with no instances open.
As in my output:
> sysop1@1204-a:~$ sudo ls -la /var/lib/apt/lists/lock
-rw-r----- 1 root root 0 Aug 23  2012 /var/lib/apt/lists/lock

edit: just now looked at my output with synaptic running - the file size remains at zero, will have to think up another way to see what is generating the file lock error.[INDENT=2]
what can I say[/INDENT]
[INDENT=3]one step at a time

[/INDENT]

---

### Post by steeldriver on 2013-05-08
... you could try

```
sudo lsof /var/lib/apt/lists/lock
```

---

### Post by mahmoud moosa on 2013-05-09
> **steeldriver said:**
> ... you could try

```
sudo lsof /var/lib/apt/lists/lock
```

Hello my friend,

Please take a look at the screen shot.

Thank you.

[ATTACH=CONFIG]242357[/ATTACH]

---

### Post by steeldriver on 2013-05-09
well since (according to lsof) no process claims to be owning /var/lib/apt/lists/lock (it is a 'stale lock') I don't see any reason you shouldn't just remove it

```
sudo rm /var/lib/apt/lists/lock
```

---

