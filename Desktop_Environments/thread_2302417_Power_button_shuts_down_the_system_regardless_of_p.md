---
title: "Power button shuts down the system regardless of power manager setting"
date: 2015-11-10
forum: Desktop Environments
---

### Post by er-ku on 2015-11-10
In power manager, I've set my system to ask me what to do upon pressing the power button.

This works nicely, with one really ugly exception: it doesn't work if the screen is locked. In that case, the system just kills all programs and shuts down.

For example, I wake my system from sleep and go to another room. When I'm back, the screen is already off, so I just press the power button without much thinking, expecting the computer to wake up or just turn on the screen. Instead, I get a shutdown in my face, losing all the unsaved changes I may have done, all browser windows, etc.

Needless to say, I find it very annoying. Is there a way to disable this misbehavior?

What I want the power button to do, is to either just turn on the screen (if it was off), or to actually ask me what to do (if it was on). At worst, the system could go back to sleep/hibernation (if the screen was on).

Thanks!

---

### Post by yoshii on 2015-11-10
check your computer's BIOS settings for power managment and/or ACPI options.  you might need to make or undo some changes there.

---

### Post by er-ku on 2015-11-11
Hardly. Like I said, the setting works as expected unless the computer is locked (even though it's locked without a password), for example, after resuming from hibernation. In that case, the computer just shuts down gracefully.
Plus, I haven't really changed anything in the BIOS recently. This seems to me more like a bug in Xubuntu.

---

### Post by flocculant on 2015-11-11
can confirm that

[s]```
ubuntu-bug xfce4-power-manager
```

Link it here please.[/s]

After talking to a couple of people in -team.

This isn't a bug with xfpm, more the way that systemd deals with this.

At the login screen xfpm no longer has control. 

You could try ubuntu-bug systemd but not sure if you'll get far.

Incidentally - if you press the button at first login - regardless of locking screen - I suspect you'll see exactly the same behaviour.

---

### Post by er-ku on 2016-03-09
Oops, I haven't been following this thread properly.

IMO, the fact that xfpm doesn't have control is irrelevant from the user's point of view. This behavior might not be a bug per current design, but in that case I say it's a flaw in the design itself. As a user, I expect that my power management settings will be respected, but they are not.

---

