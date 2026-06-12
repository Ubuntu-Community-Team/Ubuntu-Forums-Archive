---
title: "Tweak startup scripts in 10.04"
date: 2010-09-21
forum: Desktop Environments
---

### Post by treacl on 2010-09-21
How does one tweak startup scripts in 10.04?

As I understand it, some startup processes are managed by upstart and others by SysV. Sysv-rc-conf and BUM allow you to manage SysV scripts but not upstart jobs. Is there any tool (graphical or text-based) that will give an integrated view of both types of scripts?

Failing that, can someone point me toward a guide about how to identify which upstart jobs are running at startup and then temporarily disable unneeded jobs?

Many thanks,
treacl

---

### Post by kerry_s on 2010-09-21
i think you need to read up on what your messing with cause upstart replaces sysv.
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

personally, i don't think it needs messing with. if you look in the system monitor, view-> all processes
there's not much running that don't need to be.

if it were me & i wanted to stop something, i would just add it to rc.local.

example: stopping cups
**service cups stop &**

yeah, it's that simple.

---

### Post by treacl on 2010-09-22
Thanks!

If I understand your example correctly, you are killing cups after it  has started. That comes with a performance penalty, though, and I am  very impatient at boot! What I'm looking for is how to prevent an unneeded service from starting at all.

Here's what I think I've figured out: There is no /etc/inittab file, so, as you say, SysV init is not itself running. upstart does all the starting, using the scripts in /etc/init. One of these, /etc/init/rc-sysinit.conf, starts those services that still use the older-style, as-yet-unconverted scripts in /etc/init.d and /etc/rcX.d. Am I correct so far?

The question is then how to prevent unneeded scripts of either type from running. For the scripts in /etc/init.d and /etc/rcX.d, the README appears to give the answer:

"To disable a service in this runlevel, rename its script in this directory so that the new name begins with a 'K' and a two-digit number, and run 'update-rc.d script defaults' to reorder the scripts according to dependencies." (from /etc/rc2.d/README)

There is no README in /etc/init, and the man pages for init, initctl, and upstart don't give an answer. There is some information at [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html). If I had to guess, I would say to comment out the start line in the appropriate script, e.g. in /etc/init/tty6.conf:

#start on runlevel [23]

But I wonder if this is correct and sufficient...

---

### Post by kerry_s on 2010-09-22
how about, if you don't need it uninstall it & it won't be there to run.

synaptic is the best tool for the job.

---

### Post by treacl on 2010-09-22
I appreciate the suggestion, but that doesn't quite do it. Some things need to be available to run if triggered by an event, but I might not want them to run automatically at startup.

Can anyone who is familiar with upstart and the relation between old- and new-style startup scripts chime in on this?

---

