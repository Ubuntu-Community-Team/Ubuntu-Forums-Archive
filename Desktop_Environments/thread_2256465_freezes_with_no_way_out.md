---
title: "freezes with no way out"
date: 2014-12-12
forum: Desktop Environments
---

### Post by trav9595 on 2014-12-12
I have been trying lxde and it wont log out....???? Even if I go to the terminal and command it still will only work once in awhile.
And if I cant logout ,I cant use my computer because I might need XFCE to get to some sites....   what the heck is going on???
This is dangerous... so I am not going to use it anymore...but it should be fixed... 
is there another lite weight desktop that is fast and doesnt screw up like this????
and how can I delete ldxe from the list of selections that is on the log in scree<</???

---

### Post by egeezer on 2014-12-13
Have you tried the Magic SysRq Key technique?

Press and hold the Ctrl+Alt+SysRq keys while pressing these other keys in sequence, waiting a few seconds after each press:
R, E, I, S, U, B

At the end of that sequence your machine should reboot.

Yes, it takes a weird bunch of finger stretches, but it usually works.

To remove LXDE as a desktop, you can use Synaptic and take out what you don't want.  You could also do a purge of it, but that sometimes throws out stuff that you might need for other desktops.

---

### Post by trav9595 on 2014-12-13
this works

pkill -SIGTERM -f lxsession

---

### Post by Bashing-om on 2014-12-14
trav9595; Humm ...

Maybe take a look at " /etc/init/tty1.conf " see what is set :
```

cat /etc/init/tty1.conf

```

On my xfce4 system:
> 
sysop@1404mini:~$ cat /etc/init/tty1.conf
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345] and (
            not-container or
            container CONTAINER=lxc or
            container CONTAINER=lxc-libvirt)

stop on runlevel [!2345]

respawn
exec /sbin/getty --noclear -8 38400 tty1
sysop@1404mini:~$

Where I have been doing some touch ups.

Also check:
```

cat /etc/init/control-alt-delete.conf

```

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

