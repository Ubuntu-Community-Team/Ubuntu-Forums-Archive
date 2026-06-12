---
title: "Fonts Look Ugly After Update"
date: 2006-08-03
forum: Desktop Environments
---

### Post by gmcauley on 2006-08-03
Today I noticed that all my fonts seemed ugly (as if anti-aliasing is not working).  I am using Kubuntu and under Appearance - System Settings -> Fonts, anti-aliasing is enabled.

I did a big update through Adept where ~115 kde packages where upgradeable.  I suspect that somehow some font configuration files got overridden.  Perhaps my anti-aliasing configuration got changed??

Does anyone have know where I can find font configuration files and/or what might be happening?

This may sound trivial but my computing experience seems seriously lacking without pretty fonts :(

---

### Post by ihoka on 2006-08-04
I have the same problem. Had a big update the other day and now font smoothing is broken in certain apps: Gaim and Adept (in root mode) are notable.

---

### Post by gmcauley on 2006-08-04
As I look further at the KDE 'Appearance - System Settings - Fonts' panel, it looks like indeed all of the font settings were changed from what I had before (I had made changes here several months ago).  Also the anit-aliasing configuration seems to be changed.

I just changed these back to what I think I had before, and things look fine again. :) 

So, I guess the update must set the fonts to default settings.

---

### Post by kaveraj on 2006-08-10
had the same problem. followed the instructions and got it rectified.
thanks.

during that big update, I noticed another problem too.. there was some config file change in some updated package.. kdmrc IIRC; and the updater was asking which config file to use in the console embedded in the adept. But adept was not waiting for any input and hence failed to complete the update. after trying 3/4 times, i went to synaptic and fixed it. 

if adept can't accept input to its embedded console, then it is going to be a major problem. am i missing anything?

---

### Post by editrix on 2006-08-10
> **kaveraj said:**
> had the same problem. followed the instructions and got it rectified.
thanks.

during that big update, I noticed another problem too.. there was some config file change in some updated package.. kdmrc IIRC; and the updater was asking which config file to use in the console embedded in the adept. But adept was not waiting for any input and hence failed to complete the update. after trying 3/4 times, i went to synaptic and fixed it. 

if adept can't accept input to its embedded console, then it is going to be a major problem. am i missing anything?

It was kdmrc, if we have the same issues. I posted about it:

[http://www.ubuntuforums.org/showthread.php?t=230411](http://www.ubuntuforums.org/showthread.php?t=230411)

but didn't get a reply. I used Synaptic, so got the error message I did.

Can I ask what "instructions" you followed? Because I don't think my font setting look any different.

---

### Post by CyberAngel on 2006-08-12
Same problem here......

Any solution???

---

### Post by kaveraj on 2006-08-18
> **editrix said:**
> Can I ask what "instructions" you followed? 

I do not remember exactly.. I think I ran the "Reload" package list and clicked "Apply".. There were some other updates and while updating them, kdm update was rerun and things got fixed.

Usually when a package is not properly configured, apt remembers its state and reconfigures it on successive updates. I think that is what happened here.

---

### Post by Copter on 2006-08-22
hi!

had the same problem after major update. i did this :

Appearance - System Settings -> Fonts, anti-aliasing  -> disable
Apply
Appearance - System Settings -> Fonts, anti-aliasing  -> enable
Apply

it did the trick. it seems to be like before update (Kubuntu 6.06 default i think)

copter :]

---

