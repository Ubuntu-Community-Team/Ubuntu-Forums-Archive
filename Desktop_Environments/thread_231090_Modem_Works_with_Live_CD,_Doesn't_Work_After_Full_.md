---
title: "Modem Works with Live CD, Doesn't Work After Full Install...Huh?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by cubdukat on 2006-08-06
After spending some time away from Ubuntu, I decided to go back to it from Suse 10.1, which I found to be a total disappointment that never should have gone out the door. First, however, I used it as a Live CD, and found that my stubborn external modem which refuses to work in just about every distro I've tried worked without a hitch.

Not so after the full instal.

After the full install, I had the exact same problem I've always had. When asked to dial, the "TR" light comes on, but it makes absolutely no attempt to dial anything. In fact, it can't even be seen by Ubuntu; I've taken to just selecting /dev/ttyS1 since that's what it's connected to. 

I've tried checking and resetting the permissions for /dev/ttyS1 and /var/lock and assuring that I'm part of every single group that could possibly want access to the modem. In addition I've tried turning DTR on and off on the modem using &D0 through &D3, but it's not working.

Lest anyone think that this should really go in the networking section, my real question is this: How is it possible that hardware works with the Live CD, but doesn't work once Ubuntu is fully installed? 

If you've ever come across this problem, how have you resolved it? I really like how easy Ubuntu is to use and work with compared to Suse, but I really don't want to have these battles. I just want something that works out of the box like XP, but isn't XP. As much as I hate XP, they at least have the hardware detection and config better sorted out. If I can't get this straightened out, I'll probably end up dumping Linux altogether, since it's virtually useless without an Internet connection.

---

### Post by cubdukat on 2006-08-08
Well, I resolved my problem, and it was incredibly simple:

I switched which serial port the modem was physically connected to. 

The modem now works both with the Live CD and with the full install. now all I have to do is get Netzero up and running and I'm in business. man, will I be glad to be working again so I can get back with Dialup4less.com. The only reason I went with NZ is that they offered the dialer.

---

