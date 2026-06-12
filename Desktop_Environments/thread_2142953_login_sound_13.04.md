---
title: "login sound 13.04"
date: 2013-05-07
forum: Desktop Environments
---

### Post by BcRich on 2013-05-07
Hi,
this may sound like a really trivial question but I'd really like to know how to disable the sound that ubuntu plays at the login screen. it sounds like a tambala drum (if i've got the name right, sort sounds like a bongo drum but deeper) being hit once.
it's basically the sound that occurs at the login screen when you click a users name to login and the login dialog slides down to reveal a password entry box.
(try googling that)
anywayz, i found stuff on how to disable the login screen sound and the startup sound but not this particular sound, which is VERY loud on my system especially when my studio monitors are turned on.
Thanks for the help :)

---

### Post by BrunoLotse on 2013-05-07
Hi,I am using Ubuntu Tweak. Then the path Tweaks  - Sound -(Event Sound, Play Login Sound, Input Feedback Sounds, Sound Theme).Cheers,Bruno

---

### Post by BcRich on 2013-05-07
Hi BrunoLotse,
thanks 4the reply, i already tried that. unfortunatey it didn't turn the sound off. if i knew the name of the soundfile i could peraps replace it with something less erm... envasive (for want of a better word). any ideas?
thanks :)

---

### Post by BrunoLotse on 2013-05-07
Hi Rich!Another path on Ubuntu Tweak. Tweaks-Login Settings-Play Login Sound. I set it to OFF.Cheers,Bruno

---

### Post by BcRich on 2013-05-07
> **BrunoLotse said:**
> Hi Rich!Another path on Ubuntu Tweak. Tweaks-Login Settings-Play Login Sound. I set it to OFF.Cheers,Bruno

tehe, already found that one didn't work either. but thanks anyway for the suggestion Bruno :)
Ubuntu Tweak does not seem to have any effect on my login screen, I even tried changing the background image though it but that didn't work either. i wonder if it's editing the login settings for some other DM? my current login screen seems to be controlled by LightDM (standard Ubuntu Unity), but I'm not entirely sure as I'm also using KDE and XFCE. You wouldn't happen to know of a way of determining which DM is controlling my login screen, or perhaps this info is irrelevant?

strange, cause i remember this used to be quite a trivial issue. i must have messed some settings up somewhere.... but where?

---

### Post by BrunoLotse on 2013-05-07
Sorry Rich ;( I am using just straight Gnome Shell.

---

### Post by BcRich on 2013-05-07
np Bruno. thanks 4the help, i really appreciate it :) I'll post back here with any updates.

---

### Post by grahammechanical on 2013-05-07
Hi. I am using Ubuntu Unity 13.04 so I do not know if this is any help for Kubuntu but at usr/share/sounds/ubuntu/system-ready.ogg is where I find that log in sound. There must be a script somewhere but I have not found it. I would guess that the login sound is part of Ubuntu universal access requirements. It tells non-sighted people when they are at the login screen.

I remeber testing 12.04 ISO images and one of the tests was to install as a non-sighted person (cover the screen) I had to mark this test a failure because sound was muted. It was fixed in 12.10 with sound set at half way.

Edit: I have just found something else. And again I do not know how appropriate it is for Kubuntu. In 13.04 we have dconf editor. If I open that and gp to com>canonical>unity-greeter among the options I see is play-ready-sound.

No. That does not stop the sound even with a restart. 

Regards.

---

### Post by BcRich on 2013-05-07
Awesome! Thanks a mill grahammechanical. I'd previously read another thread pointing to the same sound you noted but that turned out not to be the login sound I was getting, there are however other sounds in a similar location usr/share/sounds/ubuntu/stereo/ which is where bell.ogg resides. this is the file I've been looking for. So thank for pointing me in the right direction :)

my solution was a bit hacky but it does the job, 
copy bell.ogg to the desktop. open it in audacity and use the gain filter to reduce the volume to -50 (this renders the sound in audible), then simply replace the original sound
```
sudo cp ~/Desktop/bell.ogg /usr/share/sounds/ubuntu/stereo/
```
tested it at login and quiet as a mouse :)

---

### Post by masonmouse on 2013-05-08
I found the login sound rather annoying as well and was surprised they removed any easy way to disable it. My solution was to:

```
cd /usr/share/sounds/ubuntu/stereo/
sudo mv system-ready.ogg system-ready.disabled
```

That may be a bit easier than changing the sound file itself plus you have a quick option to reenable it by just naming the file (actually a lnk) back to the original name.

---

### Post by BcRich on 2013-05-09
Thanks masonmouse, that is a much simpler solution :)

---

### Post by prose on 2013-11-11
rather than trying a workaround, have you tried editing (as SU):

usr/share/gnome/autostart/libcanberra-login-sound.desktop

there is a line there that you can change to:

X-GNOME-Autostart-enabled=false

and that should turn off your login sound.

---

