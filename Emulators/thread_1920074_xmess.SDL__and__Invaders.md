---
title: "xmess.SDL  and  Invaders"
date: 2012-02-04
forum: Emulators
---

### Post by honeybear on 2012-02-04
Hi, I have tried this command and get a weird result:

Normally SDLMESS does not support zipped ROMs or ROMs with spaces in the filename. 

```

 xmess.SDL --version ; xmess.SDL a2600 -cart spaceinvaders.a26

warning: no mixer plugins available
xmess (SDL) version 0.106 (Nov 29 2009)
warning: no mixer plugins available
info: trying to parse: /etc/xmame/xmessrc
error: unknown option sysinfo_file, on line 11 of file: /etc/xmame/xmessrc
   ignoring line
error: unknown option messinfo_file, on line 12 of file: /etc/xmame/xmessrc
   ignoring line
error: unknown option fuzzycmp, on line 30 of file: /etc/xmame/xmessrc
   ignoring line
error: unknown option skip_disclaimer, on line 32 of file: /etc/xmame/xmessrc
   ignoring line
info: trying to parse: /home/slonebun/.xmess/xmessrc
info: trying to parse: /etc/xmame/xmess-SDLrc
info: trying to parse: /home/slonebun/.xmess/xmess-SDLrc
info: trying to parse: /etc/xmame/rc/a2600rc
info: trying to parse: /home/slonebun/.xmess/rc/a2600rc
mess/systems/a2600.c: a2600 has empty ROM region (warning)
mess/systems/a2600.c: a2600 has empty ROM region (warning)
xmame: could not connect to socket
xmame: No such file or directory
LIRC disabled
done
Driver requires that device cartridge must have an image to load
devices_init failed

```

any ideas why it does not work this xmess.SDL?  xmess.SDL shall work since it is into the repositories... :( 

:popcorn::KS

---

### Post by disturbedite on 2012-02-04
You're trying to use a piece of software that has been long dead and no one supports it. Use the newer version SDLMESS.

Source code is available here: [http://www.mess.org/downloads](http://www.mess.org/downloads)

Or

PPA: [https://launchpad.net/~darkmoon/+archive/ppa](https://launchpad.net/~darkmoon/+archive/ppa)
(Unfortunately, the packaged version contained here ^ is a bit outdated but it is the only result I could find in the PPAs).

---

### Post by Liduario on 2012-06-25
I was getting this error message when using just -cart game as you've done. 

Then I tried the full path to the game and everything worked!

So the command is

xmess a7800 -cart FULLPATHTOTHEGAME

In my case: xmess a7800 -cart /home/user/Download/Mooncresta.a78

Don't use just -cart Mooncresta.a78 even if you're in the right directory.

---

### Post by Liduario on 2012-06-25
> **honeybear said:**
> Hi, I have tried this command and get a weird result:

Normally SDLMESS does not support zipped ROMs or ROMs with spaces in the filename. 

```

 xmess.SDL --version ; xmess.SDL a2600 -cart spaceinvaders.a26

warning: no mixer plugins available
xmess (SDL) version 0.106 (Nov 29 2009)
warning: no mixer plugins available
info: trying to parse: /etc/xmame/xmessrc
error: unknown option sysinfo_file, on line 11 of file: /etc/xmame/xmessrc
   ignoring line
error: unknown option messinfo_file, on line 12 of file: /etc/xmame/xmessrc
   ignoring line
error: unknown option fuzzycmp, on line 30 of file: /etc/xmame/xmessrc
   ignoring line
error: unknown option skip_disclaimer, on line 32 of file: /etc/xmame/xmessrc
   ignoring line
info: trying to parse: /home/slonebun/.xmess/xmessrc
info: trying to parse: /etc/xmame/xmess-SDLrc
info: trying to parse: /home/slonebun/.xmess/xmess-SDLrc
info: trying to parse: /etc/xmame/rc/a2600rc
info: trying to parse: /home/slonebun/.xmess/rc/a2600rc
mess/systems/a2600.c: a2600 has empty ROM region (warning)
mess/systems/a2600.c: a2600 has empty ROM region (warning)
xmame: could not connect to socket
xmame: No such file or directory
LIRC disabled
done
Driver requires that device cartridge must have an image to load
devices_init failed

```any ideas why it does not work this xmess.SDL?  xmess.SDL shall work since it is into the repositories... :( 

:popcorn::KS

I'm new to the Forum. So I decided to quote you're post in the hope you'll get a notification.

---

