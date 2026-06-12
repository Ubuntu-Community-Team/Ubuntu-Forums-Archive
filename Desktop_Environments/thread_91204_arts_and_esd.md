---
title: "arts and esd"
date: 2005-11-16
forum: Desktop Environments
---

### Post by supenguin on 2005-11-16
I've ended up running quite a mix of GNOME and KDE apps, which is an issue since my sound card doesn't support hardware mixing :(

The worst problem I ran into is that when trying to play back mp3 in amarok using arts, there was this horrible skipping echo kind of effect. The solution that ended up working: have arts pipe its audio through esd.  This way, any apps that use either esd or artsd should work.

I've only run into one problem with this: I put a link to esd in my $HOME/.kde/Autostart folder, but I believe that gets run after the rest of kde starts up, so I get this nasty error that artsd is using the null output driver every time I log in. Is there a better way to do this?

---

### Post by mlomker on 2005-11-17
I was going to suggest using Xine with amaroK but that's before I realized you need esd for mixing.

---

### Post by jpkotta on 2005-11-17
I do the reverse.  I use neither GNOME or KDE, so this code is from my ~/.xsession file.

```
# start the sound server(s)
exec artswrapper -s 2 &
sleep 3
exec artsdsp esd -nobeeps &
```

---

### Post by supenguin on 2005-11-21
I decided to try xine for playback in Amarok and am using artsd for as much as possible. That seems to work alright for now.

---

