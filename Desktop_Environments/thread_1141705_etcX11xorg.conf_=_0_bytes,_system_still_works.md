---
title: "/etc/X11/xorg.conf = 0 bytes, system still works"
date: 2009-04-28
forum: Desktop Environments
---

### Post by Niniel on 2009-04-28
Hello,

I upgraded my notebook from 8.10 to 9.04. I have an ATI Mobility Radeon 9600 card, and it works very nicely, with Normal desktop effects and all. On the other hand, my desktop has an ATI X800 card and there I don't get desktop effects. Never had them since I started with 7.10.
So I figured I'd be clever and see what xorg.conf looks like on the notebook, and maybe copy the relevant sections. However, I found out that the file is empty, and is 0 bytes in size. 
Now I'm wondering why the system is still working (if it boots, but that's a different issue). Is the real xorg.conf in some other directory? Do I have to look at a totally different configuration file altogether?

Thank you.

---

### Post by Jose Catre-Vandis on 2009-04-28
Unless you put an xorg.conf in place, of your own configuration, xorg server maanages your display settings automatically. You can get an idea of the settings by reviewing the /var/log/Xorg.0.log file.

---

### Post by markbuntu on 2009-04-28
xorg.conf has been deprecated by the X consortium. All xorg.conf functions have been automated and/or moved to utility applications.

---

### Post by Niniel on 2009-04-28
Thanks for the replies!
Do you also know where things are stored these days, if anywhere? Or does xorg server test the hardware every time I boot now?

---

### Post by Namtabmai on 2009-04-28
It tests everytime you boot. Well not test really, it looks at what hardware you have and uses that to configure itself.

You can still override this in xorg.conf thou.

---

### Post by Niniel on 2009-04-28
Ah, cool.
Maybe I should try to boot my desktop with an empty xorg.conf then.

Thank you.

---

### Post by hictio on 2009-04-29
They are the freaking elves, man :D
Take a look at this too [Where is the stuff inside xorg.conf?](http://ubuntuforums.org/showthread.php?t=1109251)
It is somehow spooky, if you will, because on the /var/log/Xorg.0.log file, it says that it uses the configuration file /etc/X11/xorg.conf which, as we know, its empty.

---

