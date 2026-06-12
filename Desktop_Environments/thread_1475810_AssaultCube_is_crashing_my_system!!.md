---
title: "AssaultCube is crashing my system!!"
date: 2010-05-07
forum: Desktop Environments
---

### Post by _0R10N on 2010-05-07
Hi everybody! Yesterday I installed AssaultCube from the repositories. I started the game and, after 2 or 3 minutes, it crashed my system. A hard reboot was the only choice I had. Those crashes continued happening every single time I tried to play the game. Very dissapointed I decided to uninstall it and download it from its website. What guess what?? I continues crashing my system.

I'm tired of hard rebooting my laptop (for obvious reasons), so I would greatly appreciate some help with this!.

I've read that Compiz could be causing this problem, but stopping it didn't prevent my system from crashing after a few minutes of playing the game.

I never got to play for more of 2 or 3 minutes.

```
compiz stop
```
This is how I'm stopping compiz.

Kind regards!

---

### Post by _0R10N on 2010-05-08
Well, I tried a few things without any luck. About an hour ago I cannot even boot my system after a hard reboot!! :mad:

I had to boot from an old LiveCD of Jaunty I have and restore my filesystem with
```
sudo e2fsck -fCp 0 sda1
```

I think I'll give up an try some other game.

Right now I'm about to download Alien Arena...

---

### Post by mgmiller on 2010-05-08
Even if you think your keyboard is locked up, try holding the alt and sysreq (print screen) keys down and while holing them hit the following letters one after the other:  rseiub.  That should do a safe shut down of the system without the stresses of a hard boot. 

The mnemonic for this is Raising Skinny Elephants Is Utterly Boring.  

You could also try resetting the x server (used to be ctrl /alt/ backspace) by doing the same alt /sysreq and then the letter k.

I don't know about the freezing in the games, but the above should help to keep you from hard booting all the time.

Good Luck.

---

### Post by _0R10N on 2010-05-08
> **mgmiller said:**
> Even if you think your keyboard is locked up, try holding the alt and sysreq (print screen) keys down and while holing them hit the following letters one after the other:  rseiub.  That should do a safe shut down of the system without the stresses of a hard boot. 

The mnemonic for this is Raising Skinny Elephants Is Utterly Boring.  

You could also try resetting the x server (used to be ctrl /alt/ backspace) by doing the same alt /sysreq and then the letter k.

I don't know about the freezing in the games, but the above should help to keep you from hard booting all the time.

Good Luck.

:lolflag: I didn't know about the first one! I'll give it a try next time!

Many thanks!

---

