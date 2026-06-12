---
title: "opengl games problem with compiz"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by icechen1 on 2008-02-17
Hi,I don't know if anyone can help me fix this annoying problem when I run some games with Compiz enabled.I have a Intel 945GM with the 'intel'' driver using AIGLX.
When I open games with compiz the game screen blink especially if there is an animation in the window behind it.
screenshot: 
[[IMG]http://img253.imageshack.us/img253/769/screenshotsh7.th.png[/IMG]](http://img253.imageshack.us/my.php?image=screenshotsh7.png)
That is what happens if i try to move the game window.
Thanks.

---

### Post by chavanak on 2008-02-17
The tearing problem!!! I normally used to see them in videos and now in games. Since you don't have a dedicated gpu, i recommend disabling compiz when running games. Press Alt+F and type in metacity --replace to turn compiz off and compiz --replace to turn it on.

Even better would be to disable woobly windows plugin and try. For diabling compiz, you can also try compiz switch (try googling it out)

---

### Post by icechen1 on 2008-02-17
> **chavanak said:**
> The tearing problem!!! I normally used to see them in videos and now in games. Since you don't have a dedicated gpu, i recommend disabling compiz when running games. Press Alt+F and type in metacity --replace to turn compiz off and compiz --replace to turn it on.

Even better would be to disable woobly windows plugin and try. For diabling compiz, you can also try compiz switch (try googling it out)

Even if i disable wobbly window the window still blinks when there is an animation in the window behind it.Yes i disable compiz when i game or watch videos but it gets annoying to often switch it on and off.

---

### Post by chavanak on 2008-02-17
run compiz in terminal and see if there is any error....

---

### Post by icechen1 on 2008-02-17
> **chavanak said:**
> run compiz in terminal and see if there is any error....

> icechen1@icechen1-laptop:~$ compiz
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
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/texture_filter. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/texture_filter. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/backgrounds/bianca-blue.png

i am using Linux Mint by the way

---

### Post by chavanak on 2008-02-17
I don't see any major erro!!!! From how long is the problem present???? 
Sorry...I guess the compiz -switch is your only solution.

---

### Post by icechen1 on 2008-02-17
> **chavanak said:**
> I don't see any major erro!!!! From how long is the problem present???? 
Sorry...I guess the compiz -switch is your only solution.
Probably since i started to use compiz(from feisty)
Thanks anyway.
Also,i can also use the appearances>visual effects tool to turn off compiz.

---

