---
title: "annoying problem"
date: 2010-04-10
forum: Desktop Environments
---

### Post by widggman on 2010-04-10
There's something very annoying that happen and i want it to stop!

There's something (that is not me), that can deactivate the "Extra" in the "Visual Effect" in the appearance. And I have to reactivate it... and then, reactivate some stuff in Compiz.

So why is there something that has the power to remove this at random (specially when switching back from fullscreen to normal in VLC) ? And, most important, how did I get rid of that something that shouldn't be able to happen once and for all ?

---

### Post by km0r3 on 2010-04-10
In what manner is this "problem" annoying you?

---

### Post by widggman on 2010-04-10
because each time it happens... I have to reset the Extra Visual Effect and some stuff in Compiz... and it shouldn't be happening. Sometimes... more than once a day! Even if it's only 30 seconds to put everything back... it's not a reason to accept this!

---

### Post by stoush on 2010-04-10
This is how I manage my Compiz settings:

1. Under System Tools->Compiz Fusion Icon
Starting this will put an icon for Compiz Windows Manager on the top right of your panel. This allows me to quickly change what WM to use, and quickly go to Settings manager which is the short cut to the full set of Compiz Settings if you really want to tweak things.

2. The broad brush of tweaking under Visual effects. But changing things here does 'stick' for me, regardless what programs I am running unless it's the Compiz Settings Manager.

Sounds like option 2 is not working out for you, maybe try option 1?

cheers,

---

### Post by widggman on 2010-04-10
but my problem is not with compiz... it's the fact that something can deactivate the "Extra" in the "Visual Effect" tab in "Preference -> Appearance"...

if that thing stops from happening... I won't have to setup things again in Compiz!

---

### Post by marshmallow1304 on 2010-04-10
When you edit the settings using CompizConfig Settings Manager, the settings in Appearance Preferences are deactivated since they are no longer in use.  Those settings (Normal, Extra) are just presets.

---

### Post by widggman on 2010-04-10
In that case, I just don't understand why adding an icon will stop this from happening... and in System Tools, I don't have anything about Compiz Fusion, is there another place where I can get it?

is it the same thing that I can have in System->Preference ?

Because, the only two options that became deactivated in Compiz are Cube Desktop and Rotate Cube... the rest is reactivated automatically after I put back the "Extra" in "Visual Effect".

---

### Post by widggman on 2010-04-11
So, it happens again... this time after deactivated the screen saver... so, it looks like anything that as the capacity to go fullscreen can screw up these setting for no reason!

Also, I tried to simply reactivate stuff in Compiz... but everything is fine... the problem is strictly with "System -> Preference -> Appearance", then in the "Visual Effect" tab, I have to reactivate the "Extra". Then, for no good reason, it has to recheck my drivers (the same that I have since the beginning... maybe with some updates). Then, because it was reactivated, it screws up stuff in Compiz that I have to reactivate because I put the Extra back on!

---

### Post by widggman on 2010-04-11
a potential solution... is it possible to change the permission of the configuration files so that only the super-user can change it ?

this way... I doubt that leaving something that was fullscreen might be able to alter the settings!

---

### Post by stoush on 2010-04-11
I added the package:
fusion-icon, description: tray icon to launch and manage Compiz Fusion
this is the one I mentioned in Option 1.

You should be able to find it in the package manager.

Really strange about the visual effects though... feel your pain must be annoying, but I cant replicate here on my machine.

---

