---
title: "Odd hang on boot and shutdown"
date: 2006-01-14
forum: General Help
---

### Post by LanceRushing on 2006-01-14
[SIZE="4"]The Problem.[/SIZE]

Several of the boot daemons are hanging on boot.
```

 * Configuring network interfaces....

```
Strange that was working, but no big deal.  So I ^C it.
Then,
```

 * Setting up X server socket directory....

```
Hangs again.... (grr...)  ^C again.

Then,
```

 * Starting system log daemon....

```
Hangs again.... (double grr)  ^C = nothing.  ^C^C^C nothing.

<ctrl><alt><del> to reboot.  It starts shutting down.
```

 * Disabling power management....              [ok]
 * Stopping internet superserver....                [ok]

```
Then nothing.  shutdown/reboot does not continue.

[SIZE="4"]What I was doing.[/SIZE]

I was testing out gforge. I had [FONT="Courier New"]apt-get install gforge[/FONT] but it failed (something about configuration didn't run).  I thought the configuration failed probably because I had an /etc/gforge directory already when I was trying to install it from source.

I removed the /etc/gforge and I tried to re-install gforge using synaptic with the 're-install' option.  But synaptic errored out b/c it couldn't connect to the apt repository.  

Weird.

So I [FONT="Courier New"]ping google.com[/FONT], and ping just hangs, doesn't respond to ^C.  (GRRR) I start another terminal, and try to [FONT="Courier New"]sudo su -[/FONT], and it just hangs.

Luckily (?) I had some ssh connections to this box from another machine that were already su'ed.  I killall ping to free up the terminals.  Already established connections work, but I can't establish new network connections .  I [FONT="Courier New"]ifconfig eth0 down[/FONT] and [FONT="Courier New"]ifconfig eth0 up[/FONT]  (thinking its a network problem).  nada.

So I reboot.  And the system hangs on shutdown (as described above).  So I have to hard reboot it.  Then it hands on startup (as described above).  Maybe it's a disk issue.  I boot off a live cd.  run a fsck on the partition.  (passes).  I mount the parition and check disk space, only 8 gigs used.  Tripple check log files for being too big, nothing.

Try to reboot again, same hang.  

I can boot to recovery mode, but still have to ^C 'network interfaces', and 'X server socket'.  And when I still hang on halt (as described above).

Any idea on what to check next.  (Sockets/devices (?))

Kernel: 2.6.12-10-686
Hardware: Basic toshiba laptop (works great for linux)

---

### Post by LanceRushing on 2006-01-15
**Fixed the problem**

It was ldap that installed with gforge.

I tracked down the problem by steping through X socket init.d script.  The command which was hanging was a chown.

[FONT="Courier New"]chown username filename[/FONT] worked but
[FONT="Courier New"]chown userid filename[/FONT] would hang.

After thinking about what changed in the permission system.  I realized that several ldap packages where installed (slapd etc).

I used aptitude to **PURGE **all the ldap packages. And then everything worked.

---

