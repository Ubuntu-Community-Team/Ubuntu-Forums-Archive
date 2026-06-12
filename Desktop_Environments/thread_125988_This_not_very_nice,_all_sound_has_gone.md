---
title: "This not very nice, all sound has gone"
date: 2006-02-05
forum: Desktop Environments
---

### Post by Watcher on 2006-02-05
Ok when I booted my computer this morning all was fine. I could play sound and there was no problem what so ever. BUT when I booted my computer about an hour ago suddenly my sound card whas no longer detected :s. I rebooted and during boot it showed "setting up ALSA device 1" and then number 2 which is normal, but still no soundcard detected when I log in.

I then tried running alsamixer which produced this error:
> alsamixer: function snd_ctl_open failed for default: Permission denied
however if I do "sudo alsamixer" it just works fine.
I really don't know what the problem is but I would really really like to get this working again :s.

Ah before i forget: I have an onboard soundsystem on my mainboard, but I don't use it, alsamixer -c1 is my Creative Audigy 2 ZS which Is the one I normally use as default.

I've got absolutly no clue as to how to fix this :cry:

---

### Post by taurus on 2006-02-05
After increasing volumes with "sudo alsamixer," run

sudo alsactl store

---

### Post by Watcher on 2006-02-05
That doens't seem to be doing anything :???:

---

### Post by taurus on 2006-02-05
It is supposed to save your settings after you run the "sudo alsamixer!!!"

---

### Post by cwaldbieser on 2006-02-05
[QUOTE=Watcher]Ok when I booted my computer this morning all was fine. I could play sound and there was no problem what so ever. BUT when I booted my computer about an hour ago suddenly my sound card whas no longer detected :s. I rebooted and during boot it showed "setting up ALSA device 1" and then number 2 which is normal, but still no soundcard detected when I log in.

I then tried running alsamixer which produced this error:

however if I do "sudo alsamixer" it just works fine.
I really don't know what the problem is but I would really really like to get this working again :s.

Ah before i forget: I have an onboard soundsystem on my mainboard, but I don't use it, alsamixer -c1 is my Creative Audigy 2 ZS which Is the one I normally use as default.

I've got absolutly no clue as to how to fix this :cry:[/QUOTE]

Can you check if your user is still a member of the "audio" group?

---

### Post by Watcher on 2006-02-05
Ok, I found the solution now: apparently i lost my acces to audio systems and had some setting wrong. Just put back all my settings and everythings works fine now :)

Thanks for all the info and tips !

---

### Post by PlatinumPlus on 2006-02-06
[QUOTE=Watcher]Ok, I found the solution now: apparently i lost my acces to audio systems and had some setting wrong. Just put back all my settings and everythings works fine now :)
[/QUOTE]

What was wrong with the settings?

---

