---
title: "Preventing from asking for password after suspend"
date: 2009-03-02
forum: Desktop Environments
---

### Post by agostonbejo on 2009-03-02
Hi!

When I put my desktop machine (a Dell, btw.) to "suspend" mode, it keeps asking for a password after returning from it, as if I had locked the screen. I would like this not to happen, I just want to return to where I was when I wake the computer up.

Can anyone help?


I did google around for a solution, but didn't find much, except for these two things (but neither of them worked):

a) 
/etc/default/acpi-support:

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

- commented it out, still the same behavior

b)
KPowersave:

configure / general settings / lock screen:

"Lock screen before suspend or standby" - I unchecked the checkbox - no change in the behavior.




Thanks in advance,
Agoston

---

### Post by kestrel1 on 2009-03-02
Instead of commenting out the LOCK_SCREEN=true, did you try changing the true to false?
Only a shot in the dark.

---

### Post by agostonbejo on 2009-03-05
Thank you for trying. ;) Your guess really makes sense, but unfortunately it doesn't work. 

Any other ideas, anyone?

---

### Post by kestrel1 on 2009-03-05
I assume this is a 8.10 machine.
I have just looked but cannot see anything that jumps out.

---

### Post by agostonbejo on 2009-03-06
I don't know whether it matters, but this is actually a feisty (Kubuntu 7.04) system. (I could have mentioned it in the original post, sorry...)

---

### Post by karamazov on 2009-04-09
Anyone find a solution to this? I've been tinkering around with no luck.

---

### Post by James Keating on 2009-05-13
At least in the standard Ubuntu Gnome session, you can bypass the requirement for entering a password on suspend/resume this way:

1. run gconf-editor (NOT as root -- gconf-editor edits per-user settings)
2. navigate to apps / gnome-power-manager / lock
uncheck the locks for suspend and hibernate, and everything else
4. go to desktop / gnome / lockdown
disable lock screen

Other situations:

To bypass the requirement for a password on boot and go straight to your session:
Go to System, Preferences, Login Screen and choose automatic login.

To bypass the requirement for a password for network access (on top of the password a router may require):
The first time keyring asks to set a password, 
1. Set nothing in either blank, click OK
2. Confirm at the panicky dialog that you do want to use unsafe mode

You may have to do this all over by deleting current passwords. Passwords are stored in /home/(you)/.gnome2/keyrings

Thanks to the various people who figured this out, including the following poster.

No thanks to the people who decided that even single-user systems must require these passwords. Root access, of course. The keyrings are useless and annoying, and should be disabled by default unless one chooses to set up a multi-user system with restricted access.

---

### Post by bearcat66 on 2009-11-04
> **James Keating said:**
> At least in the standard Ubuntu Gnome session, you can bypass the requirement for entering a password on suspend/resume this way:

1. run gconf-editor (NOT as root -- gconf-editor edits per-user settings)
2. navigate to apps / gnome-power-manager / lock
3. uncheck the locks for suspend and hibernate, and everything else

Thanks to the person who figured this out, in one of the other posts with a suspend tag.


I found the following more effective (at least in ubuntu 9.10):
as per above: run gconf-editor; navigate to desktop - lockdown, then tick "disable_lock_screen" key

---

### Post by boballen55 on 2009-12-24
> **bearcat66 said:**
> I found the following more effective (at least in ubuntu 9.10):
as per above: run gconf-editor; navigate to desktop - lockdown, then tick "disable_lock_screen" key

That would work but not only will it prevent the screen from locking after suspend it won't let you lock it manually.  Which maybe one might still what to do.

---

### Post by victor.cighir on 2009-12-25
> **James Keating said:**
> At least in the standard Ubuntu Gnome session, you can bypass the requirement for entering a password on suspend/resume this way:

1. run gconf-editor (NOT as root -- gconf-editor edits per-user settings)
2. navigate to apps / gnome-power-manager / lock
3. uncheck the locks for suspend and hibernate, and everything else

Thanks to the person who figured this out, in one of the other posts with a suspend tag.

This does not work for me on a fresh Ubuntu 9.10 . 

Luckily post #8
> **bearcat66 said:**
> I found the following more effective (at least in ubuntu 9.10):
as per above: run gconf-editor; navigate to desktop - lockdown, then tick "disable_lock_screen" key
does work. Maybe you cannot lock your screen , but at least there's no password each time you wake from suspend.

Thanks bearcat66

---

### Post by Zorael on 2009-12-25
(The thread is tagged **[COLOR="RoyalBlue"][kubuntu][/COLOR]**, so I'm assuming the OP wanted a KDE solution.)

At least in 9.10 and 4.3 (as well as in 4.4b2), unchecking 'Lock screen on resume' in System Settings, Advanced tab -> Power Management stops it from locking upon resume.

With this disabled and kernel mode-setting enabled, my machine is pretty snappy at waking up - if anything the slowest component is the touchpad, but it's also up and running within a second or two.

---

### Post by Norm24 on 2010-07-17
Just did a clean install of Lucid on a Gateway laptop.Having used the previous suggestions by bearcat and James many times before(including Lucid)
I cannot resume from suspend without entering a password on this install!

Any ideas?

---

### Post by shakma on 2010-07-29
> **James Keating said:**
> At least in the standard Ubuntu Gnome session, you can bypass the requirement for entering a password on suspend/resume this way:

1. run gconf-editor (NOT as root -- gconf-editor edits per-user settings)
2. navigate to apps / gnome-power-manager / lock
uncheck the locks for suspend and hibernate, and everything else

After a clean install of Lucid (10.04) on my new Eee PC 1005, I got interested in disabling the password after suspend.  The original method above worked perfectly.  Just two steps, and now my netbook resumes from suspend in approximately 1 second and I'm right back where I was when I closed the lid.  And since I've had this thing suspend for 24 hours with a negligible battery drain, this gives me an instant-on traveling Ubuntu machine!

Thanks, James Keating.

Peace.
shakma

---

