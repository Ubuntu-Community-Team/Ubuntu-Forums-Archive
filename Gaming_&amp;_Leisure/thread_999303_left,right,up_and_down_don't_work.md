---
title: "left,right,up and down don't work"
date: 2008-12-01
forum: Gaming &amp; Leisure
---

### Post by garrethdk on 2008-12-01
After installing jscalibrator and kxmame , the buttons on the gamepad work fine (in jscalibrator and using jstest)  but when i load a rom in kxmame the left right up and down don't work , i didn't have this issue when i was on 8.04 

Any ideas ?
Cheers
Garreth
ubuntu(8.10)

---

### Post by grossaffe on 2008-12-02
jscalibrator is the sucks and will cause problems.  You may have to uninstall it.

---

### Post by grazed on 2008-12-02
i have the same issue in zsnes.

are you running 64bit by chance?

---

### Post by garrethdk on 2008-12-02
i'm running  Ubuntu 8.10 - the Intrepid Ibex 32-bit, 
going to uninstall jscalibrator and see how i get on 
will post an update

---

### Post by garrethdk on 2008-12-02
uninstalling jscalibrator and reboot made absolutely no difference , can't understand why the buttons work but not left,right,up and down ?

Garreth

---

### Post by dfreer on 2008-12-02
> **garrethdk said:**
> uninstalling jscalibrator and reboot made absolutely no difference , can't understand why the buttons work but not left,right,up and down ?

Garreth

jscalibrator is most likely the problem here still, you may not have gotten rid of it correctly. I believe there are some configuration files that need to be removed as well. Those symptoms (buttons working but directional pad/joysticks not working) have been reported many times by jscalibrator users.

Try some of these links, see if they help you in fully removing jscalibrator (make sure to reboot your PC again as well!):
[http://ubuntuforums.org/showthread.php?t=729049](http://ubuntuforums.org/showthread.php?t=729049)
[http://snes9x.com/phpBB2/viewtopic.php?p=25185#25185](http://snes9x.com/phpBB2/viewtopic.php?p=25185#25185)

---

### Post by grossaffe on 2008-12-02
> **dfreer said:**
> jscalibrator is most likely the problem here still, you may not have gotten rid of it correctly. I believe there are some configuration files that need to be removed as well. Those symptoms (buttons working but directional pad/joysticks not working) have been reported many times by jscalibrator users.

Try some of these links, see if they help you in fully removing jscalibrator (make sure to reboot your PC again as well!):
[http://ubuntuforums.org/showthread.php?t=729049](http://ubuntuforums.org/showthread.php?t=729049)
[http://snes9x.com/phpBB2/viewtopic.php?p=25185#25185](http://snes9x.com/phpBB2/viewtopic.php?p=25185#25185)

I think you're right.  I remember something about a config file lingering and screwing stuff up after jscalibrator is removed.

---

