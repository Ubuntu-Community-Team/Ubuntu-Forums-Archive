---
title: "Turning off X..."
date: 2005-05-03
forum: Desktop Environments
---

### Post by tommy04 on 2005-05-03
Is there a way to turn off X and go back to the terminal? CTRL+ALT+BACKSPACE just goes back to GDM...

---

### Post by mlmurray on 2005-05-03
Well, you could try this;

`sudo /etc/init.d/kdm stop`, from a  terminal.

I'm not sure why, but it seems every runlevel (except 0, and 1 and 6) starts the gdm/kdm service (Actually, the appear to all start the same services).  I thought most distros usually had a multi-user, text only, run-level (usually 3) and a graphical, multi-user runlevel (usually 5).  Then you can change the default run-level in /etc/inittab to change what runlevel you boot into.

Anyone know why Ubuntu/Kubuntu is like this?  Is Debian this way also?

Here's a snippit of inittab from Mepis:

```

# Default runlevel. The runlevels used by Mandrake Linux are:
#   0 - halt (Do NOT set initdefault to this)
#   1 - Single user mode
#   2 - Multiuser, without NFS (The same as 3, if you do not have networking)
#   3 - Full multiuser mode
#   4 - unused
#   5 - X11
#   6 - reboot (Do NOT set initdefault to this)
#
id:5:initdefault:
```

Notice it references **Mandrake**. Interesting ...

---

### Post by mlmurray on 2005-05-03
Also, and forgive me if you already knew this, you can get to a terminal by doing a "CTRL+ALT+F[1..6]".  

 "CTRL+ALT+F7" puts you back in X.

---

### Post by crane on 2005-05-03
I would be interested in how to stop X as well? I never realized that the inittab file was different untill now. All other distros I have messed with have 3 as a non X multiuser mode. This was you could just sudo or su to root and type init 3 and you would stop the X server.

Could some one point me to a place to read why this is different? I'm not complaining, I'm just wondering why and what purpose it serves!!
Thanks

---

### Post by az on 2005-05-03
.... and Ubuntu uses gdm, not KDM.  Kdm is in kubuntu.

sudo /etc/init.d/gdm stop 
will turn off X.

---

### Post by mlmurray on 2005-05-03
> .... and Ubuntu uses gdm, not KDM. Kdm is in kubuntu.

Quite right.  Sorry about that.  That's why I referred to kdm/gdm on the next line.

I suppose all we'd need to do `sudo rm /etc/rc3.d/S21gdm`.  Then gdm wouldn't start in runlevel 3.  
But you might want top put a kill script in the /etc/rc3.d/ directory (K01gdm).  This way, if you change into runlevel 3 from a graphical runlevel, it will stop the gdm service automatically.   I'm not sure but you could either link to the /etc/init.d/gdm script manually  (ln -s /etc/init.d/gdm /etc/rc3.d/K01gdm) or run `update-rc.d gdm stop 3` (I'm not 100% sure this is the right command, you may want to consult the man page).

---

