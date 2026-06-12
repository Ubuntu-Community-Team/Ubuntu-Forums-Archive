---
title: "how to build RDP thin-client under Ubuntu?"
date: 2009-01-16
forum: General Help
---

### Post by mrtn86 on 2009-01-16
I would like to build RDP thin-client under Ubuntu. My envision about the final result is fallowing: user turns the computer on and it boots directly into Windows Server logon screen. So far I have installed Ubuntu 8.10, modified GRUB to boot directly into Ubuntu system without any delay waiting for user input and installed rdesktop. But what next? I would like to avoid desktop environments if possible and keep the system as thin/minimal as possible. However, any ideas how to go on? :rolleyes:

---

### Post by veloce on 2009-01-22
> **mrtn86 said:**
> I would like to build RDP thin-client under Ubuntu. My envision about the final result is fallowing: user turns the computer on and it boots directly into Windows Server logon screen. So far I have installed Ubuntu 8.10, modified GRUB to boot directly into Ubuntu system without any delay waiting for user input and installed rdesktop. But what next? I would like to avoid desktop environments if possible and keep the system as thin/minimal as possible. However, any ideas how to go on? :rolleyes:

You could just use a purpose built distro.  e.g. Thinstation.  We have that working here for exactly the purpose you describe and it works very well.

Otherwise, building on what you've done, you can add rdesktop to the auto run for the default user that you are running.

Unfortunately, my experience is that this works poorly.  What I ended up doing was putting a BIG button for rdesktop in the centre of the gnome screen.

All in all, Thinstation was the answer for us!

---

