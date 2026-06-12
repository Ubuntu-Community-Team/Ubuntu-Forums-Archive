---
title: "ESD shagged, how to reconfigure?"
date: 2005-12-13
forum: General Help
---

### Post by senectus on 2005-12-13
ESD seems to have had shagged itself, and now I can't log into gnome without killall -9 esd 
Is there some way to reconfigure it so it can set itself up for my new on-board card?

---

### Post by senectus on 2005-12-15
bump... surely someone has a tip?? :-/

---

### Post by bb002 on 2006-01-09
oops posted this in the old "Gnome hangs at brown screen after GDM login" thread...


since you are getting esd errors in the /tmp folder i would suggest dropping to a terminal with "alt+ctrl+f1" logging in as someone that can do "sudo".

type in
```

sudo /etc/init.d/gdm stop
sudo killall -9 esd
sudo rm -rf /tmp/.esd*

```
Now try running esd. restart gdm with "sudo /etc/init.d/gdm start"

[edit]....My code tag got screwed up.[/edit]

---

### Post by senectus on 2006-01-09
Apologies but I have solved this by putting my SBLive back in and using that instead of the onboard sound.

But just for the completeness of things I did delete _everything_ in the /tmp/ directory with no effect. (yes while ESD was not running)

---

### Post by bb002 on 2006-01-09
Oh alright. I'm still going to dig around. I happen to be planning to get a new sound card soon (when I say soon I mean around June :) ) so I'll keep you updated if I find anything.

---

### Post by qBaz on 2006-05-02
[QUOTE=senectus]ESD seems to have had shagged itself, and now I can't log into gnome without killall -9 esd 
Is there some way to reconfigure it so it can set itself up for my new on-board card?[/QUOTE]

I'm seeing precisely the same behaviour on my Breezy box -- a particular user's GDM login screen hangs at a blank brown screen unless and until I kill -9 the running 'esd' process, at which point login continues normally.  If I take the user out of the "audio" group, login is normal, but there's no sound.  (the genesis for this change was my using the "Multimedia Selector" to change this user's sound output to ESD... clearly, in hindsight, a mistake.)

I've changed the "Multimedia Selector" for this user back to OSS and ALSA, and I've tried removing this user's .gconf and .gconfd directories entirely, but to no avail.  I'm pulling my hair out trying to figure out where the Multimedia Selector stores its configs, and why ESD keeps getting invoked.

In the meantime, I've unchecked "Start sound server at startup" in the sound preference pane, and that's allowed me to get on with my life, at least for today.  Annoying, though.

---

### Post by key134 on 2006-12-08
I am apparently dredging up old threads tonight.  Any fix for the esd problem where you have to killall at login?  I am using edgy, so this seems to affect a lot of the releases, when it does happen.  Any help woud be appreciated.

Keith

---

