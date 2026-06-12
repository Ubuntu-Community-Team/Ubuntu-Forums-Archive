---
title: "compiz shut off itself"
date: 2010-02-16
forum: Desktop Environments
---

### Post by widggman on 2010-02-16
Hi,

  I just don't know what happen but sometimes, the special effects of "Apparence" just turn itself off. And also the option of the cube and the rotational cube in compiz are deactivated.

  It happened mostly when I open a new program or quit the full screen or VLC. In this case, all open windows go back to the first desktop.

  Is there a way to stop that from happening? It's very annoying and mostly, it shouldn't happen, not application or anything should be able to deactivate the special effects and options in compiz.

  Thanks

W

---

### Post by warp99 on 2010-02-17
Install the CompizConfig Setting Manager (CCSM) using Synaptic or the Software Center. Open CCSM, it's under System > Preferences, scroll down and enable the workarounds plugin. At the top tick the box marked "Legacy Fullscreen Support" and the "QT Window Fix" workaround since VLC does use QT.

Edit: Once you do this don't use the "Visual Effects" menu in the "Appearance Preferences" dialog box. Only use CCSM.

---

### Post by widggman on 2010-02-17
Thanks... I've just set this up... thanks again!!

---

### Post by widggman on 2010-02-20
Hi,

  It didn't work. The "extra" in the visual aspect has deactivated itself automatically... is there a way to set that thing to the root, so no application executed under my user will change that ?

  I try that to .config/vlc/vlcrc... but it's not enough...

  So any suggestion to prevent that??

  Thanks again

W

---

