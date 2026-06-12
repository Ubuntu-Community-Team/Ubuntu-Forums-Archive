---
title: "Cannot logon to GUI; gdm"
date: 2011-05-11
forum: Desktop Environments
---

### Post by uBuddhu on 2011-05-11
Alright. A little background. This all started when I had no sound being detected by my laptop's mic. I also have an external USB sound card and it was not detecting mic sound either. I had previously done recording with Audacity (it could have been back in Ubuntu 8.04).

Now, I had a feeling that I was going to break something trying to get the mic to work. Sure enough, **I'm at the point now where I cannot logon to the GUI (gdm).**

I made a number of changes before my last reboot. Here's a summary of what I think is the primary cuase (pulseaudio!):

At one point, I had lost sound altogether (I believe this was a result of having installed pulseaudio Volume control, which someone used to unlock and configure their mic).

So, things were starting to degrade. Being the persistant and stubborn one that I am, I decide to trudge on. 

I had read enough suggestions (and desite enough "didn't fix" responses), I decided to try removing pulseuadio altogether. After rebooting, I was not able to log on.

Let me try to describe this logon situation as clearly as possible:
When the laptop boots up, it shows the Ubuntu logo with the colored dots below moving from right to left (orange/white).

When I get to the user logon screen, it's not as *fancy* as it normally is. The logon window which allows me to select the user is a little more basic and the background is a simple black/purple color. The day and time is displayed on the task bar below as well as a power icon with options to suspend, restart and shut down.

This is how the logon screen used to look:
[http://beginlinux.com/images/ub904/desktop/kl_sess2.gif](http://beginlinux.com/images/ub904/desktop/kl_sess2.gif)

I've been unable to find a screenshot of the current state and I don't think I'll be able to post one due to my technologically limited situation.

When I select my user and enter the password, The screen goes blank (or displays what appears to be the console for CTRL+ALT+F1) and then I'm back at the user selection as described above as if I hadn't even tried to log on.

At this point, I'm not positive which distro I'm using, nor which kernel, but survey says:

uname -r
2.6.32-31-generic

lsbrelease -a
Ubuntu 10.04.2 LTS

My laptop is a Pavilion zd8000. 

lspci shows I have:
VGA compatible controller: ATI Technologies Inv M22 [Mobility Radeon X300]

I'm not sure if this is proper. When I run /etc/init.d/gdm stop, I get:
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop.

Probably not, because when I try sudo service gdm stop, it returns:
stop: Unkown instance.
OK. Maybe it's OK, because running sudo service gdm start, I returned back to the logon screen.
(But, I'll include this because it may indicate something, but I think it may be the way the "service" works now...)

(I do have networking enabled, so I can run apt-get and what not)

I find this interesting. I installed kdm. I started it after stopping gdm (through the service command as noted above). I was able to log on through kdm, but I'm not brought to a desktop, only a black background and a terminal window in the upper-left corner, without any window frames (I can't min/maximize/close). There doesn't appear any way to log out...

I'm not exactly sure where to go from here. I'm getting more interested in a backup/reinstall, but I may not have the ability to do that on hand, so I'd like to try to get things working. At the very least, I'd like to be able to log on and do work. Sound would be nice and a working mic would also be nice, but I can do without either of those two for now.

_Most of the solutions I've been able to find in terms of not being able to log on has been a result of:_
[B]- Bad usernames/passwords
- Insufficient drive space to allow logon[/B]

While I haven't tried creating any new users and logging on with them, I'm confident it wouldn't do any good.
df -a shows: /dev/sda1 Available = 6324296. Should be enough for basic operations.

My plan at this point is to start woking on the kdm angle. Since I am able to log on, but only to a terminal window, perhaps I can find some info on why that happens...

---

### Post by uBuddhu on 2011-05-11
vi /etc/X11/xorg.conf:

~
~
~
~
[New File]

This could be bad, no?

I ran ls in /etc/X11 and found there was a backup of xorg.conf and copied it to xorg.conf.

Result: Ubuntu is running in low graphics mode!
Error: (EE) VESA: Kernel modesetting driver in use, refusing to load (EE) No devices detected.

At this point, I was able to create a new configuration and chose to create a new one based on hardware (instead of default option), after which I was asked to reboot.

It came back with same low graphics error. I tried a new configuration with default options this time. 

This has me back to square one. (and there doesn't seem to be an xorg.conf again)

This could be another unfamiliar behavior? Xorg independence?

---

### Post by uBuddhu on 2011-05-12
I ran through the instructions for part A here (to re-enable pulseaudio):
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

That didn't help.

I'm still without audio and cannot logon.

I'm going to see if I can't get some logs of my attempt to logon to see what's happening there...

---

### Post by uBuddhu on 2011-05-12
last message in /var/log/messages before reboot (for my reference):
```
May 11 21:26:38 laptop kernel: [    22.753480]  ADDCONF(NETDEV_UP): wlan0: link is not ready
```

After trying to log on, the following appeared in /var/log/messages

```
May 11 21:30:47 laptop kernel: [    270.499395] __ratelimit: 30 callbacks suppressed
May 11 21:30:47 laptop kernel: [    270.499399]  type=1503 audit(1305185477.079:22) operation="open" pid=1716 parent=1243 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=/home/name/.profile"
```

Hmmm. So it is looking like a gdm issue...

Well, at this point, kdm loads to a blank screen (although I can see the cursor) while gdm acts as previously reported (like endless cycle of logons).

Interestingly, no additional messages appeared in /var/log/messages after trying to logon to kdm. Even though kdm seems to have froze and I can toggle through the various CTRL+ALT+Fx "views"

---

### Post by uBuddhu on 2011-05-12
Searching for the log messages above (profile="/usr/share/gdm/guest-session/Xsession"), I found these links:

There are a couple bugs against gdm-guest-session, which have been "fixed" showing that message:
[https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/282132](https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/282132)
However, it shows to be latest on my system...
There were a couple bugs listed at launchpad.net, so I'll consider filing a bug there if it comes to it.

I'm keeping gvfs-backends in mind, because my messages are a little more complicated than those found in this link which suggests the message may be ignored:
[http://serverfault.com/questions/3393/what-are-these-strange-entries-in-dmesg](http://serverfault.com/questions/3393/what-are-these-strange-entries-in-dmesg)

More on gvfs-backends:
[http://ubuntuforums.org/archive/index.php/t-1475756.html](http://ubuntuforums.org/archive/index.php/t-1475756.html)

---

### Post by uBuddhu on 2011-05-12
In the log messages, I also noticed a number of errors:

ACPI Error (dsfield-00143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS.

I don't think this is related to this issue, but I might want to think about upgrading my BIOS:
[https://bugzilla.redhat.com/show_bug.cgi?id=491588](https://bugzilla.redhat.com/show_bug.cgi?id=491588)

---

### Post by uBuddhu on 2011-05-12
Am I starting to look like a chicken running around with no head yet? 

Alright, I'm confident I have a GDM issue. :mad:

I'm able to logon with KDM after running:

```
sudo apt-get update && sudo apt-get install plasma-desktop
```

:)

No sound, either, but I'll tackle that separately. :-k

---

### Post by uBuddhu on 2011-05-12
OK, when I log in through the simplified screen, it takes me to KDM desktop now.

While this is more of a work-around, I'll consider this fixed for now.

---

