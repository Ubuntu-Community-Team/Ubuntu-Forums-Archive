---
title: "Newbie needing help with Cube/Compiz Fusion"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by waldrepdebater on 2007-11-12
Hello, I am a complete newbie, just having installed Ubuntu 7.10 last night.  I am trying to get the 3D cube effect, but I'm running into trouble.  I finally managed to install Compiz Fusion and it seems to be fine.  However, none of the effects seem to work.  Going to the System > Preferences > Appearance > Visual Effectx menu I have 4 options now, None, Normal, Extra, and Custom.  I selected custom, the display flashed several times, then it went completely gray and froze for several seconds.  After about 30 seconds it unfroze with the visual effects set to "None."  I have retried this several times and the problem persists.  I assume this is the reason that none of the Compiz Fusion options work...is that correct?  What can I do to fix this problem?

Edit: Oh, I'm running Ubuntu on my Acer Aspire 5610Z notebook.  I am dual-booting Ubuntu with the pre-installed Microsoft Vista.
Edit: The laptop has an Intel dual-core processors, 512K RAM, and an Intel 945 graphics card

---

### Post by jimerickso on 2007-11-12
open a terminal
enter "compiz "
post output

---

### Post by waldrepdebater on 2007-11-12
OK, here is the output from the "compiz" command.

```
bill@ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Segmentation fault (core dumped)
```

---

### Post by jimerickso on 2007-11-12
go to system > preferences > advanced desktop settings
disable "video playback" plugin
then run compiz --replace in a terminal and repost

---

