---
title: "Mumble sound problem with Alien Arena"
date: 2009-12-15
forum: Gaming &amp; Leisure
---

### Post by Love2MeetU on 2009-12-15
At first, thought this would be a temporary problem but it's actually turned out to be a real frustration.

When Mumble starts first, I have sound from Mumble but not from Alien Arena. When Alien Arena starts first, I have sound from the game, but not from Mumble.

---

### Post by Love2MeetU on 2009-12-15
there are no error messages, btw.

And the efffect continues AFTER the programs have been shut down, so I suspect they both have some other process still running.

---

### Post by Love2MeetU on 2009-12-18
Any help????

---

### Post by Technophobia on 2009-12-19
What version of mumble are you using?

---

### Post by Love2MeetU on 2009-12-20
> **Technophobia said:**
> What version of mumble are you using?

It's happened with ALL of them.

I tried Mumble 1.1.6, 1.1.8, and 1.2

I've since discovered the same problem occurs with my son's PC when using Ubuntu 9.10, it appears to be related to PulseAudio.

Also Alien Arena 7.00 doesn't cause this problem, but the newer Alien Arena (7.32 & later) does. The older 2007 version of Alien Arena used SDL for sound, the 2009 version uses OpenAL for sound.

Another problem on BOTH of these PCs is there is no sound from Youtube videos, ever. This is despite huge differences in hardware. Their only commonality is the use of Ubuntu 9.10, Alien Arena, and Mumble.

I've had a lot of time for testing different settings, but no actual solutions so far with Ubuntu 9.10

I've since reinstalled Ubuntu 9.04 on my own PC for testing, but sound for Mumble still cuts out when Alien Arena is running.

---

### Post by Love2MeetU on 2010-01-01
Problem solved thanks to advice from Stratocaster on the Alien Arena forums.

The solution is posted here
[http://corent.proboards.com/index.cgi?action=display&board=aatech&thread=4544&page=1](http://corent.proboards.com/index.cgi?action=display&board=aatech&thread=4544&page=1)

---

### Post by itnet7 on 2010-01-04
The solution is definitely found in the link above, but a little elaboration could benefit our newer linux users. My system is a dell XPS 1730 and I'm running the 64-bit desktop version of Karmic.

Open Gnome-terminal and create a new file called .alsoftrc. 

```
gedit .alsoftrc
```

add the following: 

```
[general]
drivers=port
```

Save your changes in gedit, You can do Alt + F4 and hit enter to save the changes. 

In the same Terminal type:

```
gksu gedit /etc/openal/alsoft.conf
```

Find the line that says: 

```
#frequency = 44100
```

add this below it:

```
frequency = 22050
```

It should then look like this: 

```
#frequency = 44100
frequency = 22050
```

Save your changes to this file as well. You should then be able to fire up alien arena with sound!

Thanks to stratocaster from the Alien Arena and Love2MeetU for finding that post on Alien Arena Forums... In my case from trying so many things with the sound, I rebooted as my sound didn't work in game or playing anything else. It may not be necessary for you though!

Chris Crisafulli
itnet7/#ubuntu-us-fl irc.freenode.net

---

