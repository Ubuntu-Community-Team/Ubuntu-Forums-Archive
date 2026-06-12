---
title: "gksudo gedit  produces nothing - sudo gedit produces a segfault"
date: 2008-12-31
forum: General Help
---

### Post by lwhitmore on 2008-12-31
Hi

I've had a strange problem since upgrading to 8.10.  Previously I could access gedit in root mode, by prefixing the command with gksudo.  Now when I do this, nothing happens at all and I'm left at the command prompt.

If I try sudo gedit, I'm left with a segmentation fault.  Does anyone know what might be happening?

---

### Post by lwhitmore on 2008-12-31
I ran 'tail /var/log/messages' after receiving the segmentation fault and got the following;

```
[87568.676165] gedit[19018]: segfault at 0 ip b74902c3 sp bfa7695c error 4 in libc-2.8.90.so[b7419000+158000]

```

Does this mean anything to anyone?

---

### Post by drs305 on 2008-12-31
What happens if you try opening another app with 'gksudo', such as:
```

gksudo nautilus

```

sudo, gksu, and gedit are all listed in synaptic, so you could try to reinstall them without too much trouble. Reinstalling won't eliminate your personal gedit settings, some of which are stored in the ~/.gconf/apps/gedit folder. (That would be the next step.)

---

### Post by lwhitmore on 2008-12-31
*(Edit: I thought reinstalling gksu had solved this, but it hadn't)*

```
gksudo nautilus
```
... works as it should.

I've tried to mv the ~/.gconf/apps/gedit-2/ folder into a backup directory, but this has had no effect.

I've reinstalled gedit without any positive effect.

I also tried reinstalling gksu, and no luck ;)

Any ideas welcome :)

---

### Post by vladimirprieto on 2009-04-25
i got similar situation over here, but without the error message on the log.

i made a custom script for partimage, where it makes an icon on desktop.  this icon (i don't know how is called on english, but on spanish is "lanzador" wich i could translate to "starter".  2° option with right click on desktop) call my script with gksudo but it doesn't run.

if i run the script from command line it runs.  if i run "gksudo myscript" it prompts me to enter the root password.

on 8.10 and 8.04 it runs without any problem.

any help will be much apretiated.

---

