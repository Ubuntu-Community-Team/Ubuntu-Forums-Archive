---
title: "Amarok - anyone got sound?"
date: 2005-03-25
forum: Desktop Environments
---

### Post by moopere on 2005-03-25
Anyone able to be any sound at all with Amarok using either ARts or Xine engines and streaming mp3?  

Tried Hoary on a laptop and two desktops with different sound cards etc etc and only the same result.....ARts engine locks up Amarok completely and it has to be killed - Xine engine appears to work, something is streaming in and the fft display thing (or whatever it is)  at the bottom bounces around indicating audio of some type feeding in but no actual sound at all.

Other KDE sounds appear fine, using kaffeine appears to work as well.  Is Amarok broken with all engines except gstreamer (which doesn't work under KDE by the way because the amarok gstreamer engine won't play through arts!!!)??

I've tried Amarok under gnome with gstreamer engine and it works

Cheers,
Craig

---

### Post by meralon on 2005-03-26
Install the akode-mpeg package. It should work now with the arts engine.

---

### Post by apokryphos on 2005-03-26
To use one of the other engines install them from the repositories.

---

