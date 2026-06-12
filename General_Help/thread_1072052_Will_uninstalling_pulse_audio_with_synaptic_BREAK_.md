---
title: "Will uninstalling pulse audio with synaptic BREAK anything ?"
date: 2009-02-17
forum: General Help
---

### Post by brjoon1021 on 2009-02-17
Will uninstalling pulse audio BREAK anything ?

---

### Post by gettinoriginal on 2009-02-17
You need to make sure that ***_all_*** your sound settings are set for Alsa first, or you could lose sound.

---

### Post by sdennie on 2009-02-17
It won't permanently break anything, no.  However, as stated above, many or most of your apps will need to be changed to use ALSA instead of Pulse Audio or you won't hear sound coming from them.  This is usually very trivial and many, many apps can be changed to use ALSA just by selecting all ALSA settings in System->Preferences->Sound.  I've been using ALSA instead of Pulse Audio since Hardy Beta and I've never had any problems at all.

---

