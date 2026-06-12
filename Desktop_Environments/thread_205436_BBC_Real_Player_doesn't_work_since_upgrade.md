---
title: "BBC Real Player doesn't work since upgrade"
date: 2006-06-28
forum: Desktop Environments
---

### Post by jnoreiko on 2006-06-28
I used to have Real Player installed on Ubuntu, and I could listen to BBC radio shows within a Firefox window from this page: [http://www.bbc.co.uk/radio4/progs/listenagain.shtml](http://www.bbc.co.uk/radio4/progs/listenagain.shtml)
(Not all the shows launch in the browser, some are plain RAM files that open in the Real Player app)

I now still get the audio controls loading in the window (which seems to me to indicate the plugin is ok), but I get this dialog box twice:

> Could not find an appropriate hxplay or realplay in system path to use as an embedded player

---

### Post by kleeman on 2006-06-28
What does this command reveal:

which realplay

If it shows /usr/bin/realplay (as mine does) what does

ls -al /usr/bin/realplay 

give?

Mine shows 

lrwxrwxrwx 1 root root 35 2006-03-07 09:44 /usr/bin/realplay -> ../lib/realplay-10.0.6.776/realplay

BTW, the clips run for me in firefox....

---

### Post by jnoreiko on 2006-06-28
```
which realplay
```

gives no result.

Guess I have to reinstall RealPlayer then... :)

---

### Post by kleeman on 2006-06-28
Looks like it. Mine were installed from the plf repo:

[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

---

### Post by jnoreiko on 2006-06-28
I downloaded mine from the Real site itself, but now I can't seem to find where to get it again...

Good thing I never delete anything... the installer is still in my download folder :)

It runs, but firefox still gives the errors, I can't double-click a RAM file, and dragging the RAM file to the RealPlayer window seems to work, but there's no sound.

I think there's a general sound problem, because when I open an MP3, totem says "can't connect to sound server"

---

### Post by hesee on 2006-06-30
I have that same problem with realplayer :(

---

### Post by John_the_linux_newbie on 2006-06-30
hi guys,
I have a similar problem - real player used to work and not it appears to work but there is no sound.  The player indicates that it is playing a stream and not dropping packets, but no sound comes out.

I can play the same stream in Firefox and MPlayer works fine.
I checked which device is active the 0 device is an Alsa mixer and the 1 device is an Sigma Tel OSS mixer.   I've tried both with no luck.

I'm running Dapper on a Dell Latitude D600.

---

### Post by matjaz_pirnovar on 2006-07-01
Hi,

It works for me to when installing it through PLF.  Just follow instructions in above posting.

PS: I installed Real Player from Real website too and it didn't want to work. Well, now it does. :)

Try.

M

---

### Post by John_the_linux_newbie on 2006-07-03
Thanks Folks,

I originally installed real player as per the PLF instructions and everything was great.
Last week I noticed that I no longer had sound from real player although mplayer would play real streams from within Firefox.

This morning I attempted uninstall real player using synaptic however when I checked the real box in synaptic I received a message that the package could not be installed due to missing xlibs.

I checked the xlibs-dev box thinking the worst that could happen was that real would not work and the best that could happen would be that is would work again.

It works now, just as it used to.  I must have accidentally corrupted the xlibs that I had installed...well I can't say must as I am not really sure what happened or how the problem was fixed.  In any case all is well with my system now.



I had

---

