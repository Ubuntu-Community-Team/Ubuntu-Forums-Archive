---
title: "nautilus? graphic glitches in 9.04 (nvidia 180.44)"
date: 2009-06-02
forum: General Help
---

### Post by ayu on 2009-06-02
Hello,

After upgrading to 9.04, I've noticed frequent graphic glitches in the window manager, like the title bar not updating to the correct title in firefox, new files not appearing in nautilus until I manually hit refresh directory, or part of the title bar appearing to be the inactive window. In the attached screenshot, the file is saved (so the * in the title should be gone), and the title bar is colored like it is part active and part inactive. I'm using compiz and nvidia driver version 180.44. Is it a problem with nautilus, compiz, or nvidia? How can I fix this?

Thanks in advance,
Ayu

---

### Post by steeleyuk on 2009-06-02
Try disabling Compiz. I wrote in another thread the other day that there is a bug in the Human theme and/or the nvidia proprietary driver. You have similar symptoms (title bar playing up).

---

### Post by ayu on 2009-06-03
Are there any other suggestions other than disabling compiz?

---

### Post by ayu on 2009-06-08
Any other ideas? :)

---

### Post by steeleyuk on 2009-06-08
Try a different theme and/or theme engine.

Install Emerald and use that instead of Metacity.

---

### Post by ayu on 2009-06-09
> **steeleyuk said:**
> Try a different theme and/or theme engine.

Install Emerald and use that instead of Metacity.

How do I know if I'm using Metacity or Emerald? I installed emerald with compiz way back in 7.04, but I think my current theme is metacity. Would loading Emerald Theme Manager cause it to switch to emerald? Everything seems fine now even though I quitted the manager without changing anything.

---

### Post by ayu on 2009-06-12
How do I know if I'm using Metacity or Emerald? It still glitches occasionally. Thanks in advance.

---

### Post by ayu on 2009-06-15
Openoffice is really glitchy. Any ideas?

---

### Post by ayu on 2009-06-18
Please help? :)

---

### Post by Arup on 2009-06-18
Update your nvidia drivers, you can do it the hard way by downloading from nvidia's site or the easy way by adding repository from [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html) If you download from nvidia you have to follow proper procedure to install it. [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

Follow the instructions posted at this thread.

---

### Post by cascaranuez on 2009-06-26
I had exactly the same glitches, mostly on openoffice and kde apps on Ubuntu 9.04 and nvidia 180.44.

Upgraded nvidia to 180.60 and then to 185.18.14, and still the same glitches with all them.

Tryied without compiz and it draws fine, but without compiz.

Any solutions? Maybe some weird option on nvidia driver, or in compiz...

---

### Post by hibliss on 2009-06-26
Go to System>Administration>Hardware Drivers and roll the driver back to 177. I am running that with Compiz, no issues. I too had problems with 180.

---

### Post by ayu on 2009-06-29
Update to let others know how I "fixed" this:
In Compiz settings -> Workarounds -> check force sync between X and GLX.

I've tried rolling back to 177 using Hardware Drivers, and also manually installing the newest version from nvidia's site, but both didn't work for me. The above setting works for me with 180.

---

