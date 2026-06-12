---
title: "Can't switch to virtual terminal"
date: 2006-08-10
forum: Desktop Environments
---

### Post by sw1ng on 2006-08-10
I can't switch to a virtual terminal. I'm running gdm as my display manager. If I kill it (ctrl-alt-backspace) and then repeatedly hit ctrl-alt-f1 sometimes I can get a terminal, but usually not before gdm restarts. I tried adding "Option" "DontVTSwitch" "false" to my xorg.conf ServerFlags section, but it didn't make any difference.

Any idea why this doesn't work, and/or how to fix it?

Thanks.

---

### Post by mlind on 2006-08-10
This issue has popped few times before and I think someone was even able to solve it. 

Are the other tty processes running?
```

ps -A grep | tty

```

---

### Post by exif on 2006-08-10
I've been trying to solve this for a little while too :mad: 

Are you using the nvidia drivers?

---

### Post by sw1ng on 2006-08-10
I'm running fglrx, not the nvidia driver.

Here's my ps -A | grep tty (that's what you meant, isn't it?)

```

#ps -A | grep tty
 4646 tty7     00:02:36 Xorg
 5099 tty1     00:00:00 getty
 5100 tty2     00:00:00 getty
 5101 tty3     00:00:00 getty
 5102 tty4     00:00:00 getty
 5103 tty5     00:00:00 getty
 5104 tty6     00:00:00 getty

```

---

### Post by mlind on 2006-08-10
> **sw1ng said:**
> I'm running fglrx, not the nvidia driver.

Here's my ps -A | grep tty (that's what you meant, isn't it?)

```

#ps -A | grep tty
 4646 tty7     00:02:36 Xorg
 5099 tty1     00:00:00 getty
 5100 tty2     00:00:00 getty
 5101 tty3     00:00:00 getty
 5102 tty4     00:00:00 getty
 5103 tty5     00:00:00 getty
 5104 tty6     00:00:00 getty

```

Yeah, looks good so far. What modules are loaded on your /etc/X11/xorg.conf ?
Even though this looks to be nvidia related, It could help [http://ubuntuforums.org/showthread.php?t=203532](http://ubuntuforums.org/showthread.php?t=203532)

---

### Post by walovaton on 2006-11-07
While I was using dapper with nvidia binary drivers it sitched virtual consoles but it showed me a blank screen, it worked because I used it blindly and the commands I did type worked (killing some apps in the X session).

Now with edgy and nvidia binary drivers it doesn't even switch to a blank console, it just doesn't do anything.  Like if the F[n] keys were disabled or something.

I still have to check two things:
- Disabling nvidia binary drivers.
- the solution linked by mlind.

---

### Post by walovaton on 2006-11-07
Turns out that I can't disable nvidia binary drivers.  When I try to change "nvidia" to "nv" in xorg.conf the X server complains and it doesn't start.

I tried the solution linked by mlind and it didn't work either.

However, I forgot to mention that switching to a virtual terminal from GDM actually works.  The problem occurs after login into Gnome.  The only way to workaround this is switching to a virtual terminal just after starting the logging process.  It does work afterwards.

Any ideas about how to solve this annoying problem?

-William

---

