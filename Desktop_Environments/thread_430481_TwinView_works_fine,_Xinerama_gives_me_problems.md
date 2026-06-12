---
title: "TwinView works fine, Xinerama gives me problems"
date: 2007-05-02
forum: Desktop Environments
---

### Post by Flutterby on 2007-05-02
Hey all, I have a dual head Feisty setup. TwinView works fine on it, but I want to use Xinerama instead.
I added the line
```
Option "Xinerama" "on"
```to the section "ServerLayout" in my xorg.conf. It sort of seems to start up, but, the resolutions of both monitors seem to have changed, and all the windows only show as outlines on the main screen and as black rectangles on the second one. When I try to type something in them the screen repaints a few lines so you can read the text for a sec, but then it all goes back to black. Also, everything seems really slow.

Any help would be much appreciated.

---

### Post by Nythain on 2007-05-03
you are gonna have to edit your xorg.conf for xinerama setup... if you run a nvidia gksudo nvidia-settings works well for making the changes... basically it involves setting up two screens, two monitors, and two devices

---

### Post by Flutterby on 2007-05-03
> **Nythain said:**
> you are gonna have to edit your xorg.conf for xinerama setup... if you run a nvidia gksudo nvidia-settings works well for making the changes... basically it involves setting up two screens, two monitors, and two devices

Nythain: as I mentioned TwinView works fine, and in that I have two of each...

---

### Post by orb9220 on 2007-05-03
> Nythain: as I mentioned TwinView works fine, and in that I have two of each...

Nythain is correct.

The lines you have for dual are for twinview and Not xinerama which requires different lines.

Either Find the Nvidia-settings in system tools menu and if it is not there run 
nvidia-settings in a term.

---

### Post by Flutterby on 2007-05-04
I ran nvidia-settings, checked the Xinerama button, and restarted X. The result is the following. My left monitor (after the login screen) goes black and stays that way. The right monitor has the same problem as before with all the windows only showing as squares with content that appears for a fragment of a second when you type something.

...so what do I do now?

---

### Post by Flutterby on 2007-05-04
Okay... I disabled the "Translucency" options of KDE and now it works.

---

