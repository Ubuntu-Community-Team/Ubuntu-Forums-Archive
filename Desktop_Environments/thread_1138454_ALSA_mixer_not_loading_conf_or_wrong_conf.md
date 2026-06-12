---
title: "ALSA mixer not loading conf or wrong conf"
date: 2009-04-26
forum: Desktop Environments
---

### Post by Valsum on 2009-04-26
Hello!

My problem is simple. I use Xubuntu Jaunty and every time I boot the computer, mixer is at 3% volume and muted. I've tried playing with asoundconf and aumix without success in fixing it. Help, please! :)

---

### Post by benerivo on 2009-04-26
Have you tried ```
sudo alsamixer
``` then ```
sudo alsactl store
```

---

### Post by HarleyGhost on 2009-05-02
I also have the same problem. Everytime I reboot I have to unmute and turn up the volume. But when I try to run "sudo alsactl store" i get an error that says Home Directory /home/** not ours. Any ideas?

Thanks,
HG

---

### Post by Valsum on 2009-07-01
Same than HarleyGhost. What else should we do?

---

### Post by del_diablo on 2009-07-01
```
sudo apt-get remove pulseaudio
```

---

### Post by Valsum on 2009-07-02
It was so easy! Thanks.

---

