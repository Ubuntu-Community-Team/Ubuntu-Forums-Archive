---
title: "Can't Adjust Clock Time"
date: 2005-08-04
forum: Desktop Environments
---

### Post by BTJustice on 2005-08-04
I right-click once on the clock then left-click on "Adjust Date & Time".  I am asked for the root password which I know and enter.  I click OK and the clock time never opens.  What might be causing that?

---

### Post by MrCheese on 2005-08-04
[QUOTE=BTJustice]I right-click once on the clock then left-click on "Adjust Date & Time".  I am asked for the root password which I know and enter.  I click OK and the clock time never opens.  What might be causing that?[/QUOTE]

have you actually enabled the root account? It's disabled by default. Try using your own password - sudo will temporarily give you root access.

---

### Post by BTJustice on 2005-08-04
No dice.  If I open the root terminal and enter...

/usr/bin/kcmshell kde-clock.desktop

I get an error about DCOP communications but I can open the clock.  Not sure what is going on.

---

### Post by BTJustice on 2005-08-04
No one knows?  It is getting quite annoying not being able to adjust the clock in Kubuntu.

---

### Post by crt on 2005-08-23
Same type of problem here. I enabled root login because, user login blocked me from changing the time. I wish ubuntu wasn't so over bearing on security.
But anyway when I change the clock as root, I can change, my screen goes blank and my monitor says there is no signal, and then it comes back up and maybe it will be the right time or maybe it won't.
If I finally get the clock set, when I reboot into kubuntu, the clock is off again. It doesn't mess with my Windows or Linspire OS. But Kubuntu will not save the clock settings.

Rog

---

### Post by c0rderr0y on 2005-08-23
i've had a similar problem like this i just did a reinstall and it fixed it =D hopefully you havent done too much customizing yet.....  ](*,)

---

