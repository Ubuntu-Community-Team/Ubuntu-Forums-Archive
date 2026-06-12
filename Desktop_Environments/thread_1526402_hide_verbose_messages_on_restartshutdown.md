---
title: "hide verbose messages on restart/shutdown"
date: 2010-07-08
forum: Desktop Environments
---

### Post by histographik on 2010-07-08
[COLOR=DarkSlateGray]I have Lucid installed on two PCs. [/COLOR]
[COLOR=Purple]The PCs are identical except one uses the on-board Intel G33 video controller while the other has an nvidia 210 video card attached.[/COLOR]
[COLOR=Orange]The nvidia PC restarts/shuts down without showing any console text messages, however the Intel based PC has the following problem. [/COLOR]
[COLOR=SeaGreen]The software on both machines is identical (except for the nvidia packages).[/COLOR]

[COLOR=Navy]On restart or shutdown on the intel based PC plymouth gives way to a console for 2 or 3 seconds showing the following[/COLOR] 
(*none of which are errors as far as i know*)...
```
Broadcast Message from root@xyz-desktop
  (unknown) at 11:44 ...

The System is going down for restart NOW!

* Deactivating Swap ...
* Unmounting weak filesystems ...

init: Disconnected from system bus
```Plymouth then continues with the nice splash screen until the system either shuts down or restarts.

[COLOR=Orange]I know it's a very minor gui snafoo, but I'd like to understand why this is happening so I can fix it. [/COLOR]
[COLOR=Green]System is up-to-date and clean as of 2010-07-08.[/COLOR]

System Info:
> X86_64 System Asus P5KPL-AM EPU
Intel Corporation 82G33/G31 Express Integrated Video
Sources:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
deb [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubunt ]("http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu")lucid main[COLOR=Sienna]**Does anyone know how I can hide this console text output?**[/COLOR]

---

### Post by =CrAzYG33K= on 2010-07-08
[OT] Why're you even bothered? Just do yourself a favor and don't look at the screen! :popcorn:[/OT]

---

### Post by histographik on 2010-07-08
[COLOR=Sienna]Bump ... There is a real issue here, and i can't see the root of it. Anyone?[/COLOR]

---

### Post by awp2513_ on 2010-12-16
I know this is an old post, but I was wondering if you ever found a solution. I'm facing the same problem.

I haven't been able to find any information about what is generating the messages, which is sort of key to solving the "problem".

Possible solutions could include changing the text color (it will log, but the user won't see it), but ideally Plymouth would be started sooner to prevent a time when the screen is black or logging.

Any thoughts?

---

### Post by Paul E on 2011-12-22
Wanted to post a solution I came up with to this very issue. I edited /etc/rc.local and added "clear" (sans-quotes) right above the exit 0 command. This results in a black screen instead of console output.

Cheers.

---

### Post by overdrank on 2011-12-22
Thanks for the info. Back to sleep thread. Thread closed. :)

---

