---
title: "If sound (ESD) will only play as root (my solution)"
date: 2005-10-17
forum: Desktop Environments
---

### Post by brockjudkins on 2005-10-17
I was about to post a lengthy description of my sound problem, but I figured it out. I am using ESD, and after uninstalling polypaudio, only the root user could play sound.

A quick way to see if your sound card works at all (if it isn't, this post wont help you) is to type in a terminal (brace your ears, or turn down your speakers :rolleyes: ):
```

esd

```

If you hear a loud beeping sound, your card works. Type Ctrl-C in the terminal to quit ESD.


In my home directory, I ran
```

ls -la

```

and saw:
```

-rw-------   1 root root        16 2005-10-16 20:46 .esd_auth

```

So I ran (replace 'brock' with your username)
```

sudo chown brock:brock .esd_auth

```
and my problems were gone. (almost, Pingus and SuperTux didn't work, but fixed it after reading [http://ubuntuforums.org/showthread.php?p=418797#post418797]("http://ubuntuforums.org/showthread.php?p=418797#post418797"))

Don't you hate it when it's something so stupid like that? :oops:


To make this more Googleable, I'll paste in what I was originally writting, and perhaps if you are troobleshooting sound, checking some of these things out might help:

**********************************************************************

I've been trying for hours, and still can't get ESD to function properly. I did a lot of research, but haven't found the solution.

In the Multimedia Systems Selector the ESD test says:

Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'


There are some other interesting things that might serve as clues:

1. When I reboot I CAN hear the ubuntu login screen sound (the one that sounds like three bongo hits).
2. When I actually login, however, the login music doesn't play (the new-agish sound)
3. Flash in Firefox is the only thing that I could get to work


And some more mundane info:

I dont have a ~/.asoundrc file. I just have /etc/asound.conf setup like this (I am using my second soundcard):
```

pcm.!default {
type hw
card 1
}

ctl.!default {
type hw           
card 1
}
```

My /etc/esound/esd.conf is:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

When trying to play a CD in Sound Juicer, I get:

[FONT="Comic Sans MS"]Error playing CD.

Reason: Could not open resource for writing.[/FONT]

I can run "esd" in the terminal, and I get the loud beep sound, and it seems to run ok.

In /tmp, the only ESD-related thing is:

```
drwxrwxrwt   2 root  root  4096 2005-10-16 21:32 .esd-0
```

---

