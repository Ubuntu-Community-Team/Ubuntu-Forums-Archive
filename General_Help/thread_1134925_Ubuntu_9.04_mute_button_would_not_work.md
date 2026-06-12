---
title: "Ubuntu 9.04 mute button would not work"
date: 2009-04-24
forum: General Help
---

### Post by s05128 on 2009-04-24
Hi all,
I am using a Dell Inspiron 6000, just updated to Ubuntu 9.04 and my mute button on the laptop is not working. However, in Preferences-> Keyboard Shortcuts when I tried to set the sound controls, the mute button shortcut was assigned properly to "mute".

Could anyone help me please? Thanks a bunch

PS: I'm a beginner Linux user, so please apologize if there are any doubts.
:)

---

### Post by s05128 on 2009-04-25
anyone?

---

### Post by yuvattar on 2009-06-21
I believe I have the same problem. I have an HP Pavilion dv6815nr, and the mute button does work (it turns red, and the sound icon shows it's mutted), but the sound doesn't really mute. In fact, if I mute the sound from the tray icon, the same thing happens: the icon shows as muted, but the sound keeps coming. Help, anyone?

---

### Post by Arcturus691 on 2009-08-21
I think I am having the same problem. Does your volume control on the keyboard also have no effect on the volume but you can set the volume by left clicking on the volume control in the top panel?  

This problem started for me after updates in July.  I also had bad sound distortion when moving my mouse but that was fixed with the latest image update: linux-generic (2.6.28.14.19) to 2.6.28.15.20.  From what I have read it looks like ubuntu is moving to pulse audio from alsa and OSS.  One of the updates was for pulse audio which might be the issue. 

I think this is a bug but I would like to get more input before reporting it.

**Detailed problem description:**
On my system when I press the volume up/down key, the on screen volume display appears and moves in the corresponding direction.  If I press the mute key, the on screen display reflects this.  If you left click on the volume control in the top panel, the volume has not moved (IE: not in sync w/ the on screen display) and is not muted even though the OSD shows as muted.

Ubuntu 9.04 64Bit AMD64
NVIDIA NFORCE SLI CK804 ALC850
Desktop

---

