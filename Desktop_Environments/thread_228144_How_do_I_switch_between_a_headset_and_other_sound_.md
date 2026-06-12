---
title: "How do I switch between a headset and other sound card without rebooting?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by therblack on 2006-08-02
Hi

I have just got a USD headset for use with Gizmo (a plantronic 400--seems to work well).

What I want to do is have sound come out of the headset when it is plugged in, but come out of the speaker if it is not.

Alsa seems to be okay with this, but esd (and hence gnome) does not.  What seems to happen is that esd (when started from gnome) always used the 0 sound device...and this is either set when booting up or is always the headset.

Does anyone now a way to get esd to use a specific sound card?  I have tried changing the Default Sound Card setting in gnome, but that doesn't seem to affect esd.

thanks for any help

R

(PS I could have sworn that I submitted this question earlier today, but I couldn't find it in the forums, so apoliges if this is the second post)

---

### Post by bratliff on 2007-03-30
THey hid the controls. LOOK in volume control-file-change device.

ratliff

---

