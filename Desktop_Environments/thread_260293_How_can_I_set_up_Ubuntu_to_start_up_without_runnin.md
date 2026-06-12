---
title: "How can I set up Ubuntu to start up without running xserver?"
date: 2006-09-18
forum: Desktop Environments
---

### Post by buddachile on 2006-09-18
Hi.

I have a computer running Dapper that I am using as a server, so I don't need xserver running at all. I'd like to save resources while running the server so my question is how can I set it up to boot without starting xserver?


I've searched the forums but didn't find the answer.

Thanks for any help you can offer.

--
buddachile

---

### Post by mitch.c on 2006-09-18
> **buddachile said:**
> how can I set it up to boot without starting xserver?
Remove gdm from the default runlevel. Get bum (boot up manager) or sysv-rc-conf to help you do that.

---

### Post by Ibbelz on 2006-09-18
Just switch to runlevel 3. You can do that by editting you /etc/inittab file.

Look for this line and change it to 3:

```

# The default runlevel.
id:2:initdefault:

```

Just so you know the different runlevels:

```

# Default runlevel. The runlevels used by RHS are:
#   0 - halt (Do NOT set initdefault to this)
#   1 - Single user mode
#   2 - Multiuser, without NFS (The same as 3, if you do not have networking)
#   3 - Full multiuser mode
#   4 - unused
#   5 - X11
#   6 - reboot (Do NOT set initdefault to this)

```

---

### Post by tomzero on 2006-09-18
> **Ibbelz said:**
> Just switch to runlevel 3. You can do that by editting you /etc/inittab file.

Look for this line and change it to 3:

```

# The default runlevel.
id:2:initdefault:

```



How should the line look exactly after the proposed change?
id:3:initdefault  or
id:2:3 or
3

Thanks in advance,
Tom

---

### Post by ayoli on 2006-09-18
> **tomzero said:**
> How should the line look exactly after the proposed change?
id:3:initdefault  or
id:2:3 or
3

Thanks in advance,
Tom

id:3:initdefault

edit: but init 3 will run scripts in /etc/rc3.d where gdm script is also linked
```
[00:11:45@ayoli.zone]:~ >$ ls /etc/rc3.d/*gdm -l
lrwxrwxrwx 1 root root 13 2006-06-07 13:57 /etc/rc3.d/S13gdm -> ../init.d/gdm

```

---

### Post by Ramses de Norre on 2006-09-18
```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
Remove the X on the line of gdm in column 2 (or 3 if you changed your runlevel to 3).

---

### Post by ayoli on 2006-09-18
> **Ramses de Norre said:**
> ```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
Remove the X on the line of gdm in column 2 (or 3 if you changed your runlevel to 3).

actually, same as remove link to /etc/init.d/gdm from the /etc/rc<level_num_you_want>.d/ isn't it ?

---

### Post by Ramses de Norre on 2006-09-18
Yes, but if you remove the link you'll need to remember the S code in front of it if you want to restore it later, sysv-rc-conf will do this for you.

(Or you could move S13gdm to s13gdm)

---

