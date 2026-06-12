---
title: "[SOLVED] How Do I Turn off XGL?"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by aaaantoine on 2007-10-21
In Gutsy, when the package xserver-xgl is installed, it is enabled by default.  Naturally, I have forgotten the instructions on how to turn it off if I need to.  And, because compiz w/ XGL doesn't like other 3D applications, I need to turn XGL off sometimes.  How do I do this without uninstalling xserver-xgl?

---

### Post by darkshadow on 2007-10-21
Copy and paste

Xgl server setup changed

The Xgl server will now be started automatically next time you login.  It is no longer necessary to use any special X session to start Xgl, and such sessions will likely fail to work properly.  Please select a regular session from your session manager next time you log in.  To disable Xgl autostart for this user, create a file named ~/.config/xserver-xgl/disable




What problems can arise with other 3d apps. I have not found any but all I have really tried is Planet Penguin Racer which had no problems.

---

### Post by dasunst3r on 2007-10-21
Before you log in, try going to Options -> Select Session or something like that.  If you can't choose just regular GNOME, then the other place I'd probably look is System -> Preferences -> Appearance -> Visual Effects.

---

### Post by aaaantoine on 2007-10-21
> **darkshadow said:**
> Copy and paste

Xgl server setup changed

The Xgl server will now be started automatically next time you login.  It is no longer necessary to use any special X session to start Xgl, and such sessions will likely fail to work properly.  Please select a regular session from your session manager next time you log in.  To disable Xgl autostart for this user, create a file named ~/.config/xserver-xgl/disable


Thanks for pasting that for me.  I kinda missed/forgot the instructions to disable the autostart feature.

> 
What problems can arise with other 3d apps. I have not found any but all I have really tried is Planet Penguin Racer which had no problems.

Frets on Fire won't load for me, and I think XGL might be the culprit.  Screen savers will work when desktop effects are disabled, but otherwise they won't (just tested this: it's not related to XGL, apparently).

> **dasunst3r said:**
> Before you log in, try going to Options -> Select Session or something like that.  If you can't choose just regular GNOME, then the other place I'd probably look is System -> Preferences -> Appearance -> Visual Effects.

Tried that out, but note the above text pasted by darkshadow; all sessions are made into X sessions automatically.  Also, I saw no setting for XGL in Visual Effects.

---

### Post by H1tm3n on 2007-10-25
OK, I have disabled Xgl .... how do I enable it again? :):):)

---

### Post by darkshadow on 2007-10-25
To enable it again just delete "disable"

---

