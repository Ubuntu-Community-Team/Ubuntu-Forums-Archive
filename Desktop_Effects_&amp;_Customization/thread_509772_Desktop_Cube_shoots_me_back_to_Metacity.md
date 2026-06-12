---
title: "Desktop Cube shoots me back to Metacity"
date: 2007-07-25
forum: Desktop Effects &amp; Customization
---

### Post by HelloKitty on 2007-07-25
I recently (a day or two ago) installed Beryl.  All of the default features worked.  Cube, icon previews, etc.  Today I decided to open up the settings manager and tinker around (although, very artificial 'tinkering'.  Basically turning features on and off).

Soon, I was shot back to Metacity.  Selecting Beryl again, I get shot back to Metacity (the act of getting 'shot back' involves my window title bars flickering as they change window managers, a pause as they reach Beryl, and then the repeat process as they come back to the fully functioning MetaCity).

Soon I found that if I turn off the 3D cube feature I can mess around with Beryl fine.  But the *moment* I even click the 3D cube feature (I don't even have to use it, just active it under settings) I get shot back to Metacity.

I have tried to uninstall and reinstall, but I fear it may not have been the cleanest of uninstall/reinstalls.  Some googling didn't offer much either.

Thanks in advance.

---

### Post by michael37 on 2007-07-25
> **HelloKitty said:**
> I recently (a day or two ago) installed Beryl.  All of the default features worked.  Cube, icon previews, etc.  Today I decided to open up the settings manager and tinker around (although, very artificial 'tinkering'.  Basically turning features on and off).

Soon, I was shot back to Metacity.  Selecting Beryl again, I get shot back to Metacity (the act of getting 'shot back' involves my window title bars flickering as they change window managers, a pause as they reach Beryl, and then the repeat process as they come back to the fully functioning MetaCity).

Soon I found that if I turn off the 3D cube feature I can mess around with Beryl fine.  But the *moment* I even click the 3D cube feature (I don't even have to use it, just active it under settings) I get shot back to Metacity.

I have tried to uninstall and reinstall, but I fear it may not have been the cleanest of uninstall/reinstalls.  Some googling didn't offer much either.

Thanks in advance.

I am afraid your Beryl crashes and that's why you are shot back to Metacity.  That means some settings put Beryl in the corner it can't get out of.  Probably the best strategy is not only to uninstall and reinstall, but also to carefully wipe all beryl and gnome settings.

---

### Post by DaH-RaT on 2007-08-15
so how do you do that?

---

### Post by uzerzero on 2007-08-15
Are there any other 3D settings that aren't working? If that's the case, your Nvidia or ATI drivers might not be loading properly. I would test out some of the other 3D settings before doing a complete wipe of Beryl and Gnome-settings, although they probably wouldn't hurt at some point.

---

### Post by petit.padavoine on 2007-08-15
> **DaH-RaT said:**
> so how do you do that?

Uninstall beryl.

In your home directory, ```
rm -R .beryl
```

Reinstall beryl.

Also consider switching to compiz fusion

---

