---
title: "Monitor Screen on ubuntu 10.04 goes blank frequently"
date: 2010-06-23
forum: Desktop Environments
---

### Post by tim042849 on 2010-06-23
I have a new ubuntu 10.04 install, it is the third that I have done
recently. On this particular install (unlike the others) the screen goes
unexpectedly blank and any motion restores the screen. It is acting like
a screen saver with the blank screen option set. 
Even with the following settings:
Screen saver off
Lock Screen option off
All power saving functions that I can find are off.
Power saving functions in bios are off

This is an **awful** problem! My wife uses this computer
and she **hates** this. If I were to set up a computer for
a client with this problem it would be a deal breaker.

FYI:
This is a compaq presario desktop.
I am a programmer with 10 years experience in linux, redhat, slackware
ubuntu and kubuntu. I am familiar with the command line.

Please let me know how to disable or correct this feature.

If any one reading this does not know how to help, but might
have some ideas of how I might escalate support, please let me
know. 
Any thoughts at all are better than none at all. I am terribly dissapointed that I posted this earlier and got **zero** and I
mean **0** responses.
thanks
tim

---

### Post by cwintermeyer on 2010-06-24
I'm having the same problem with a fresh 10.04 LTS 32-bit install on an IBM NetVista 8301-41U. I have all screensaver and power saver options off in Ubuntu, and have disabled power saving in the BIOS. I ran Ubuntu 9 on this machine and did not have this problem.

NOTE: In my situation, it appears to be a Power Management thing (not a screen blanking thing), since the monitor goes into standby. I didn't have this problem in Ubuntu 9, and I have tested this monitor with Win7 and as an external on my MacBook Pro and it does *not* go dark with those OS'es so I don't believe it's a problem with the monitor itself.

---

### Post by sikander3786 on 2010-06-24
Hi.

It is a very strange problem to hear. Even if the screensaver is set to off the screen is going blank. Haven't heard of it so often.

Just a thought, don't swithc off the screen saver, increase the timeout and see if it gets better.

Regards.

---

### Post by tim042849 on 2010-06-24
> **sikander3786 said:**
> Hi.

It is a very strange problem to hear. Even if the screensaver is set to off the screen is going blank. Haven't heard of it so often.

Just a thought, don't swithc off the screen saver, increase the timeout and see if it gets better.

Regards.
I've tried that. No change. To make matters worse, as I was typing
this message, on my Gateway - another machine with Lucid, firefox
quit without warning. This really sucks. I had similar problems with earlier
versions of ubuntu/kubuntu. I changed to slackware 13.0 and **never**,
**ever** had such an occurance.  :p I note your signature. Ubuntu will
**never** kill M$ with stuff like this. BTW: The gateway that I am on
also has nVidia video hardware.

I'm so used to getting help directly from the slackware list, but I'm going to probably have to post directly to ubuntu's technical support.
I'll let you folks know how that goes.
thanks
tim

---

### Post by hhh on 2010-06-24
This pain-in-the-rear problem has been around for ages, hopefully this post will solve it for you...
[http://ubuntuforums.org/showpost.php?p=5380990&postcount=7](http://ubuntuforums.org/showpost.php?p=5380990&postcount=7)

xorg.conf doesn't exist by default anymore, you may have to create one and put it in etc/X11. Reboot for it to work.

Hope that helps.

---

### Post by tim042849 on 2010-06-24
Wow! Possible light at the end of the tunnel.
I will implement this as soon as I am done with this message
and confirm results.

Also, on my Gateway, I have a different problem, and I have had this
with all the versions of ubuntu and kubuntu that I have used, but
never on slackware:
1)firefox quits without warning.
2)konqueror quits without warning (less frequently)
3)ubuntu quites without warning and drops me to the login screen

Since my wife's compaq (which is the one experiencing the screen blanking)
and my gateway both have nVidia chipsets, could this fix work for the
gateway too or can you recommend another solution.
Thanks so much
tim

---

### Post by hhh on 2010-06-24
I have no idea about your other problem, but you should open a new topic for it instead of tacking it onto this thread. Mark this thread as solved if the fix works;)

---

### Post by tim042849 on 2010-06-24
> **hhh said:**
> I have no idea about your other problem, but you should open a new topic for it instead of tacking it onto this thread. Mark this thread as solved if the fix works;)
Understood.
Will start a new thread.
I will monitor my wife's computer - it will probably take some time 
before I can confirm a solution.
thanks again

---

### Post by tim042849 on 2010-06-24
:confused: Well, there is no change. Still the same symptoms. 
s**t
sigh!

---

### Post by mr clark25 on 2010-06-24
> An often suggested fix is to add the following to the **end** of you xorg.conf file:does your xorg.conf file have just those lines mentioned in it? it may need to have more... (the whole configuration)


does it do this in "safe mode"?

---

### Post by tim042849 on 2010-06-24
> **mr clark25 said:**
> does your xorg.conf file have just those lines mentioned in it? it may need to have more... (the whole configuration)


does it do this in "safe mode"?
Hi Mr. Clark (had a teacher by that name in High School)
As for your first question, the entirety of xorg.conf follows:
```

Section "Screen"
    Identifier  "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver  "nvidia"
    Option  "NoLogo"    "True"
EndSection

Section "ServerFlags"
    Option  "blank time"    "0"
    Option  "standby time"  "0"
    Option  "suspend time"  "0"
    Option  "off time"  "0"
    Option  "DPMS"  "false"
EndSection

```
Please note that the last line in the "ServerFlags" section has added
after symptoms persisted. 

As for your second question: I have not tried it in safe mode.
What I have done is put a different monitor on the computer.
As I type, and having watched the monitor some time I do not see
any blanking. 
I'll continue to watch the computer with the changed monitor and see
that happens. I know that my wife would prefer the other monitor, but
it is an "old" but very functional Mag LT565, built in 2002.
thanks
tim

---

### Post by hhh on 2010-06-25
The "DPMS" setting needs to go in it's own section named "Monitor". Also, my "ServerFlags" section is capitalized like this...
```
Section "ServerFlags"
    Option         "BlankTime" "0"
    Option         "StandbyTime" "0"
    Option         "SuspendTime" "0"
    Option         "OffTime" "0"
EndSection
```

I'm not a programmer so I have no idea if either of those changes will fix your problem.

---

### Post by tim042849 on 2010-06-25
Thanks for the code revisions, I've implemented them with no
change in the condition. I went back to the mag monitor and
it is still blanking out. But to clarify, not a problem with
the other monitor (which is a microtek).
BTW: When I added the 'monitor' section as in
```

Section "Monitor"
    Option  "DPMS"  "false"
EndSection

```
I couldn't start X on rebooting.
(corrected that by editing xorg.conf in text mode)
My poor little brain suggests that perhaps this can be resolved
in the monitor configuration, **OR** my wife will have to end
her affair with the Mag and stick with the Microtek.
I appreciate you hanging in with me here. I **am** a programmer,
BTW, but not a system programmer obviously. :lolflag:
tim

---

### Post by hhh on 2010-07-06
Sorry to revive this, but I had to do a reinstall of my Debian OS and I discovered that using  Option  "DPMS" without the "false" in the Monitor section and then adding the ServerFlags options was the right combination to disable screen blanking for me. I had to reboot afterwards  for it to work.

In case that helps anyone.

---

### Post by mirwanda on 2010-07-07
just decrease the brightness to 80% or 90%
hth

(well, you may say i am nOObish, but... at least it works on my laptop :))

---

