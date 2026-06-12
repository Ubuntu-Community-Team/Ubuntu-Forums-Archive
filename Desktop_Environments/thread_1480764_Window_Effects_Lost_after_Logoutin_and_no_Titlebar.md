---
title: "Window Effects Lost after Logout/in and no Titlebars"
date: 2010-05-11
forum: Desktop Environments
---

### Post by cebif on 2010-05-11
After upgrading from 9.10 karmic to 10.04 lucid, the windows of applications have no titlebars and I cannot move or resize them. Also if I have System, Preferences, Apprearance, Visual Effects, set to normal or extra the settings are lost after a logout/in or reboot.
I have another user login and the Vishual Effects settings are remembered with it, but with my main more priviledged user, they are not.
I sort of got around the problem by adding compiz to Startup Applications, but that only allows the Titlebars to show at at Normal or Extra settings in Appearance, Vishual Effects. It is reset to Normal or Extra when I select None before logging out/in.
Should there be a part of compiz that starts even when none Vishual Effects is selected? (to show titlebars etc) Where is the configuration file that is meant to start compiz per user? I don't think Startup Applications settings properly deal with it.

---

### Post by squab on 2010-05-12
if your using the default metacity bars <alt><f2> > metacity --replace
if that actually fixes your problem you can have it run at startup by adding it to the list of startup applications in System->Prefernces->Startup Applications

---

### Post by cebif on 2010-05-12
> **squab said:**
> if your using the default metacity bars <alt><f2> 
if that actually fixes your problem you can have it run at startup by adding it to the list of startup applications in System->Preferences->Startup Applications
<alt><f2> would not start but I used a terminal. That command brought back the titlebars and work-spaces buttons on the panel. I added metacity to Startup Applications and after logout/in I find it is fixed. Thanks for the help.

---

