---
title: "Gnome settings daemon error driving me nuts!"
date: 2008-05-30
forum: Desktop Environments
---

### Post by metrorat on 2008-05-30
Hi all... I am running Hardy on an Acer 5652WLMI with compiz & mac4lin and it looks and runs great except for the unshakeable gnome-settings-daemon error.  It used to appear nearly every time I booted but would sort itself very quickly and correct icons etc would appear a few seconds after login. Now it appears every time and I lose all my custom icons and everything runs very slowly and things like clicking the logout icon or the bar menus have no effect for a few minutes. Sometimes it seems to kick back in and the correct icons suddenly appear but this is 10 mins after login.  In fact it just happened as I am writing. Have looked on launchpad but being an ubernoob don't really understand what I'm reading.  I *have *tried btw deleting my Gnome settings folders from /~ and regretted it. After I had got things back the way I wanted the bug just reappeared. I only got it occasionally with 7.10 (bearable) but it seems to have got much worse with Hardly and worse still since the last round of updates I installed today (every boot both rt and generic kernels).

Can't seem to find any useful info as all the refs to this bug are in closed Hardy development forums and don't seem to apply to my situation.

Can anyone help me - this is heavily getting on my nerves and undermining my faith in Ubuntu.

Thanks

---

### Post by nic-stange on 2008-05-30
Hi,
could you be more specific about the gnome-settings-daemon error?
Is there a message?
Which icons are disappearing/not appearing? The ones of your gnome panel (the taskbar) or even within applications? All applications? Or are there some where eberything goes fine?

Regards 

Nicolai

---

### Post by metrorat on 2008-05-30
> **nic-stange said:**
> Hi,
could you be more specific about the gnome-settings-daemon error?
Is there a message?
Which icons are disappearing/not appearing? The ones of your gnome panel (the taskbar) or even within applications? All applications? Or are there some where eberything goes fine?

Regards 

Nicolai

Hi Nicolai - thanks for your reply. Here is the GSD error message:

There was an error starting the GNOME Settings Daemon.

```
Some things, such as themes, sounds, or background settings
may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote
application did not send a reply, the message bus security policy
blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you
log in.
```

I also get an info message after logging in which had not appeared before the latest update now does not seem to want to go away:

```
New Advanced Linux Sound Architecture (ALSA) configuration
presets have been added.  Please execute the asoundconf(1)
set-default-card macro in a Terminal now to refresh your user's
configuration presets.  You may accomplish this task by executing
the following command in a Terminal: asoundconf set-default-
card
```

Before I last restarted I entered:```


asoundconf set-default-card Intel
```

But the message still appears (its definitely the right card)

Icons-wise all are showing as Gnome defaults (see attached screenshot).  However as you can see from the terminal the mac4lin window borders are retained.  In applications all icons, buttons and window themes are Gnome defaults except for the window borders. This seems to be the case for all applications (even Firefox which has its own M4L icon set).

Right everything just kicked in again with m4l icons including apps (see second screenshot).

Also everything is v slow before the icons kick in and the taskbar takes literally a minute or more to respond. After the icons come back its still a bit sluggish but not as bad.

Any thoughts?

Cheers

---

### Post by nic-stange on 2008-05-30
See 
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)
It seems to be a DBUS problem

Try to fix it the way 
  Ric Flomag  wrote on 2008-03-30:  (permalink)  
in his comment by modifying the session startup configs.

Aleternatively just install dbus-x11. But this has some drawbacks as described in the Thread.

Which Ubuntu release are you actually using? Did this happen due to an upgrade?

---

### Post by metrorat on 2008-05-30
I've checked out that page before actually. Dbus-X11 is installed automatically with Hardy (my version of Ubuntu as above).  I think this issue has a variety of possible sources.  For example when I try and start gsd manually I get:
```
** (gnome-settings-daemon:15501): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:15501): WARNING **: Could not acquire name

```

Will keep hunting...

---

