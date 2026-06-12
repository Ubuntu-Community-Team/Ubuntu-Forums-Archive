---
title: "problem with visual effects"
date: 2007-11-30
forum: Desktop Environments
---

### Post by TheMouse on 2007-11-30
I'm running 7.10 on an Acer Extensa 5620. I cannot get visual effects to turn on at all. I read an article on fixing it and generally poked around the forum and wiki trying to find a solution. The error message is simply, "Desktop effects could not be enabled," which doesn't really suggest any solutions to me.

Thanks in advance for any help.

---

### Post by schauerlich on 2007-11-30
What video card do you have?

---

### Post by TheMouse on 2007-11-30
I believe it's an Intel Graphics Media Accelerator x3100.

---

### Post by reality1011 on 2007-12-01
What exactly are the visual effects?  I have an extensa 5620 as well and I haven't had any problems yet other then not being able to delete the ~20gb vista restore partition...

---

### Post by mdbarton on 2007-12-01
Desktop effects are enable on System -> Preferences -> Appearence and the 'Visual Effects' tab.  I have not problem running this as the main user, but the second user account also gets the 'Desktop effects could not be enabled' message.

---

### Post by dixon on 2007-12-02
It's because the card(X3100) is blacklisted. The card is quite recent and can't play videos when the effects are enabled.... You should wait for the new drivers or if you don't mind the videos you can just comment the line in /usr/bin/compiz where X3100 is blacklisted.

---

### Post by pappfer on 2007-12-11
Install XGL (xserver-xgl from Synaptic) and you will be able to enable desktop effects. ;)

---

### Post by skwerl530 on 2007-12-11
I have the same video card in my Acer laptop.  I haven't been able to try this yet but I found this thread that looks like it may work.
[http://ubuntuforums.org/showthread.php?t=506744&highlight=intel+965](http://ubuntuforums.org/showthread.php?t=506744&highlight=intel+965)

---

### Post by adityam on 2007-12-11
> **TheMouse said:**
>  The error message is simply, "Desktop effects could not be enabled," which doesn't really suggest any solutions to me.
.

I had the same error message. I realized that compiz was not installed on my computer. The effects worked after I installed compiz.

---

