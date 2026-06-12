---
title: "Same conky.img on EVERY script??"
date: 2011-09-15
forum: Desktop Environments
---

### Post by moonsal on 2011-09-15
Got a problem here.... No matter what conky script I run I always get this (the script running has absolutley nothing to do with this one either, it's a net.stat script??) All was working fine the other day then all the sudden, this ****.... WTF.. I've removed ALL conky related and reinstalled many times but to no avail... Any ideas???
Thanks in advance...

[img]http://i53.tinypic.com/120jpn8.png[/img]

---

### Post by drmrgd on 2011-09-15
I could be wrong here, but that looks like the default conky script that comes with the install.  Where are you putting your custom .conkyrc script?  You've got to have your custom .conkyrc script in  your home directory, and you've got to tell Conky where to look for it if I recall correctly.

---

### Post by Frogs Hair on 2011-09-15
That is the default Conky configuration and the only time I see it is when a mistake was made during  installation of a new configuration or I have forgotten rename  .conkyrc  if required . I have also made a typo when renaming the .conkyrc . I don't know why an installed theme would stop working unless the .conkyrc was moved one of the above mistakes was made . There may something happening with Nautilus .  gksu nautilus and see if any errors are displayed .

---

### Post by 42dorian on 2011-09-16
So, you can't get it to go away, even though you've uninstalled Conky?  Or you just can't get it to turn off?

```

sudo killall conky

```

That should kill all instances of conky, no matter who is running them.  Then you just have to make sure there's no Conky entry in any of your startup scripts.  Simple enough.  If you had it autostarting with the OS, go to your settings manager and remove it from your startup applications.

Deep breaths.  It's not a big deal.

When you want a specific conky script to run, you need this command instead:

```

conky -c ~/path/to/your/conky/script

```

Otherwise it just loads the default.  When you have your net stat script loading in Conky, you have a specific conky script you want.  You need to know where you saved it, and direct Conky to that script.  Hence the conky -c command.

If you want that to load on startup, you need to put an entry for it in your autostarted applications.

---

