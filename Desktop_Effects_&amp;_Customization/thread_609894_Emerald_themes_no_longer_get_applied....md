---
title: "Emerald themes no longer get applied..."
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by gotee12 on 2007-11-11
Hey all,

I'm running Gutsy with an ATI card. XGL, Compiz and Emerald were working beauftifully, then one of the Emerald themes I downloaded from compiz-themes.org messed things up. Now Emerald no longer instantly applies any of the themes I select. In fact, even if I restart X (by logging in/out) there is no guarantee that any theme will apply, most of the time a deleted theme keeps resurfacing after a restart of X. 

I've completely removed/reinstalled XGL and Emerald (haven't tried removing Compiz yet). I've used "compiz --replace", "emerald --replace" and even "metacity --replace" to reset it back to Gnome defaults (which worked, but when I switched back to compiz, the emerald problem was still there). I've installed the Fusion icon and even if I refresh the window manager through the icon, the theme still doesn't apply. The rest of Compiz works great (cubes, expo, etc.). I'd post my xorg.conf, but I don't know if it's simply an Emerald issue. I searched for other posts but couldn't find anything that worked. Thanx in advance for any help.

gotee12
gotee12 att gmail dott com

---

### Post by gotee12 on 2007-11-11
Obligatory bump for the night crowd....

Are bumps necessary here? On other forums they pretty much are, but here I noticed the "unanswered threads" option. Are bumps considered bad etiquette here?

---

### Post by gotee12 on 2007-11-12
Ok, I've discovered a little more. The problem may not lie in Emerald. If I open the Emerald Themer 0.3.0-svn, and click on a new theme, the "theme" folder in ~/.emerald/ properly updates with the new theme files. But the actual theme is not applied to the desktop. If I click on a different installed theme in Emerald Themer, the new theme is copied into the ~/.emerald/theme folder. But the desktop is not updated, etc., etc.

I've tried uninstalling/reinstalling eveything compiz/emerald related via a command I found on a different post (sudo apt-get purge compiz* libcompiz* libdeco* emerald* libemerald*). I then rebooted and went back into Synaptic and reinstalled everything. I've even removed/reinstalled xgl. Still no luck.

Any ideas anyone? Thanx in advance.

---

