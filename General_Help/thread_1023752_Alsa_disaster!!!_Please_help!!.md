---
title: "Alsa disaster!!! Please help!!"
date: 2008-12-28
forum: General Help
---

### Post by Makaai on 2008-12-28
Hi, I've made a disaster with alsa: I tried to install driver,libs and utils sources packages but I did not like the sound output, so I did make uninstall, and after reboot and login I got black screen! I think alsa is no more enabled...what I can do??

Edit: launching emergency terminal, if I try to use alsamixer, it says that alsa-utils is not installed, but if I try to install, it says that is already installed, so I think that is only disabled...maybe

---

### Post by randallecook on 2008-12-28
Ouch! From the emergency terminal I would try to uninstall ALSA to return to a stable system. Run 'sudo apt-get remove <alsa-package-name>' and then reboot. Once you have your normal desktop back, you can try to carefully bring sound back. Perhaps you should try a different aound architecture than ALSA, like OSS.

BTW, posting your audio hardware information might help. If you use a separate sournd card, post make and model. If audio is on the motherboard, post its make and model.

Randall

---

