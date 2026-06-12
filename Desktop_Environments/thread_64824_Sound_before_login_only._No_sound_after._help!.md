---
title: "Sound before login only. No sound after. help!"
date: 2005-09-12
forum: Desktop Environments
---

### Post by howlerbr on 2005-09-12
When the login screen appears I can hear a sound. But after I login no sound is avaiable. Do you what can be wrong? I have tried to manage the sound settings in System menu but with no success. I've tried ALSA, OSS and when I click on test it always returns that it failed. But in the login screen the sound was ok...

Do you know if I missed some configuration. My soundcard works fine in Slackware with ALSA support. It is an onboard card VIA AC'97.

Thanks

---

### Post by ispmarin on 2005-09-12
Hello:
Try to start xmms from a terminal and play something,  and post here what is displayed.

---

### Post by howlerbr on 2005-09-13
ok solved! The problem was that I was trying to make my modem to work... and I have created a file in /etc named modprobe.conf and this file was not taking account the sound modules... ](*,)

---

