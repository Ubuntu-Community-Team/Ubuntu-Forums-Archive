---
title: "boot problem: terminal instead of gnome"
date: 2006-01-06
forum: General Help
---

### Post by gosh on 2006-01-06
Hi,

I don't know what I did wrong, but my notebook will not start gnome.
When I boot everything looks fine, but it will start in terminal mode tty1.

I tried sudo dkpg-reconfigure xserver-xorg, but no succes:confused:

---

### Post by hillbilly on 2006-01-06
Did you try checking initdefault value in  /etc/inittab file and see whether it is set to runlevel 5 ? (I guess it should set like that unless you did modify it!)

---

### Post by dcast on 2006-01-06
try typing "startx" that will start x and gnome if that is indeed the problem.

---

### Post by gosh on 2006-01-06
[QUOTE=hillbilly]Did you try checking initdefault value in  /etc/inittab file and see whether it is set to runlevel 5 ? (I guess it should set like that unless you did modify it!)[/QUOTE]

it says: 
# The default runlevel.
id:2:initdefault:

Btw, the live-cd does boot normally

---

### Post by gosh on 2006-01-06
[QUOTE=dcast]try typing "startx" that will start x and gnome if that is indeed the problem.[/QUOTE]

startx gives me a grey screen, first with a cross, than with a mouse-pointer. That's all

---

### Post by hillbilly on 2006-01-06
[QUOTE=gosh]it says: 
# The default runlevel.
id:2:initdefault:

Btw, the live-cd does boot normally[/QUOTE]


Hmm...that means your default run level is 2. And 2 means its Multi-user mode (without NFS). I guess changing that to 5 should allow you to boot up in Graphical mode. Iam sorry, iam not on my linux machine and so cannot confirm that this is what I have in my inittab file. Can anyone else over ehre confirm this !!

---

### Post by gosh on 2006-01-07
It's solved.

I did sudo apt-get install ubuntu-desktop and it worked again.

... still don't know what actually happened...

---

### Post by mztriz on 2006-01-07
[QUOTE=gosh]It's solved.

I did sudo apt-get install ubuntu-desktop and it worked again.

... still don't know what actually happened...[/QUOTE]
what video card do you have?

---

### Post by gosh on 2006-01-07
[QUOTE=mztriz]what video card do you have?[/QUOTE]

It is an ATI Technologies Inc Rage Mobility P/M AGP 2x

---

