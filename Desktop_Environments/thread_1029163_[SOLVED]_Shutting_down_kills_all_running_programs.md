---
title: "[SOLVED] Shutting down kills all running programs"
date: 2009-01-03
forum: Desktop Environments
---

### Post by argie on 2009-01-03
What happens:
1. I have a few programs running all the time - evolution-2.22 and firefox-3, for example.
2. I shutdown the computer.
3. Everything shuts down immediately.
4. When I boot the next time, firefox and evolution complain that they've been improperly shutdown.

What I expect:
1. Shutting down waits for those programs to close before going on.

Or is the way it currently works standard behaviour? I cannot imagine it being so, because that's awful. Just yesterday I had this email typed up (but unsaved) and I switched to a different workspace. Forgetting about the email, I hit the shutdown button and Evolution grabbed focus and asked me if I wanted to save. However, as soon as I hit save, the computer began shutting down. The next time when I booted, no email in drafts, but Evolution thankfully offered to rescue it after complaining about being improperly shut down.

I'm using Ubuntu 8.04 Hardy Heron 64-bit.

---

### Post by nemilar on 2009-01-03
The nature of the linux shutdown process is that, once the shutdown procedure is initiated, all programs will be told to stop (issued SIGTERM, or "terminate"; this is the same as using "kill [pid]").  Those processes that don't shut themselves off quick enough will then be issued SIGKILL (the same as "kill -9 [pid]").  The scripts in /etc/rc0.d/ will be run first; these cleanly turn off all services (which is where the "Stopping [name of some service here] ............ [   OK   ]" messages come from.

Traditionally, the system administrator, when he was going to shutdown a system, would give the other users a warning, using something like 

```
shutdown -h 50
```

which prints to all terminals:

```
Broadcast message from jdeprizi@enterprise
	(/dev/pts/0) at 8:15 ...

The system is going down for halt in 50 minutes!

```

It is then the user's responsibility to close down all applications and save all data, because in 50 minutes, all processes will be KILL'd.




Not a helpful answer at all, I know :D:D  but I thought I'd try explaining why things are the way they are.

You are right, though.  It would be more user friendly if Gnome interrupted the shutdown procedure, not actually sending the shutdown command until all windows were closed.  Not sure if this is something being considered/worked on, but it would be neat...

---

### Post by argie on 2009-01-06
Thanks for the explanation. I can't say I'm happy with the way it works, maybe I should file a feature request somewhere. Just as soon as I can find where.

---

### Post by nemilar on 2009-01-06
You can post one here:

[https://bugs.launchpad.net/ubuntu/]("https://bugs.launchpad.net/ubuntu/")

I think it should be marked a Wishlist item... since it is a feature enhancement.  A rather good one, though, in my opinion.

---

### Post by bunty on 2009-01-06
Now you realise what shutdown means , what's so hard about closing ffx is you want a clean restart next time?

When you leave the house do you turn of the video and the washing machine and the computer or do you just hit the circuit breaker on the way out of the door?

You could wish for a windozey scenario where everthing starts popping up windows about "are you sure" and " are you really, really sure" but it would probably be longer than just shutting the browser when your done with one click on the little X button.

If you want simplicity, I have an easier , faster solution. I open a terminal type sync command and when I get the prompt back I hit the power. 

:P

---

### Post by argie on 2009-01-07
@nemilar: Thanks for the link. I did search launchpad first and bugs like [this one]("https://bugs.launchpad.net/gnome-session/+bug/276134") gave me the impression that this feature existed. I also distinctly remember something like this already existing.

In any case, the feature is partially provided by System»Preferences»Sessions»Session Options»Automatically remember running applications when logging out. Firefox doesn't bring up the right tabs, but that's okay, it's just the way I like it.

@bunty: Amusing analogy. But I have no desire to carry the real world's inefficiencies to the computer world. I'd rather the machine make it easier to work than emulate all the chores of reality.

In any case, here's why I needed it. I usually have Evolution open in another workspace so it can check for mail and do its thing. The old way just killed it, forcing me to have to 'Recover' each time I booted. This way is much more convenient. It doesn't interrupt shutdown, but just quits neatly. Praise be the Gnome!

---

