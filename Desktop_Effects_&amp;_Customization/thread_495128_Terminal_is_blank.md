---
title: "Terminal is blank"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by benhagerty on 2007-07-07
Just install ubuntu and then beryl, terminal is blank white, I can click stuff but it is this white box in the middle of the screen, I am sure this is a common problem, Help me ubuntu gods! 	](*,)

---

### Post by Megaqwerty on 2007-07-07
If I remember correctly, running: ```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
``` and then restarting X by doing **Ctrl+Alt+Backspace** should fix that.

-Megaqwerty

---

### Post by benhagerty on 2007-07-07
I just tried that nothing happened, I just uninstalled Beryl and restarted, nothing. I  can't drag windows and I don't have the minimize x-out boxes up the top corner of windows also

---

### Post by CorranSW on 2007-07-07
I am having the same problem... However when i hit crtl alt backspace ubuntu crashes

---

### Post by Megaqwerty on 2007-07-07
I'm sorry, I forgot to ask what cards you were using. Ubuntu doesn't crash when you do **Ctrl+Alt+Backspace,** it just restarts X (The graphical environment.) Anyways, there is another way to fix this problem. You need to open up your xorg.conf file: ```
gksudo gedit /etc/X11/xorg.conf
``` and find the words DefaultDepth, and make sure it looks like this: ```
    DefaultDepth    24
``` Save, and exit, then either restart X again with **Ctrl+Alt+Backspace** or restart your computer. The problem should be fixed now.

-Megaqwerty

EDIT: If this solves your problem, please got to "Thread Tools" and mark this thread as "Solved", this will make it easier for people with the same problem to find the solution.

---

### Post by benhagerty on 2007-07-08
I changed it from 16 to 24, no luck. anything else?

Edit: Also, when I open Beryl, it makes the wall paper black and everything messed up

---

### Post by hyperair on 2007-07-08
Make sure you have this line:
```

Option "AddARGBGLXVisuals" "True"

``` in your "screen" section.

---

### Post by benhagerty on 2007-07-08
> **hyperair said:**
> Make sure you have this line:
```

Option "AddARGBGLXVisuals" "True"

``` in your "screen" section.
Thanks! I have terminal working! Now I have a new problem, I went to gimp to scale down an image and when I clicked open the window turned black. What is wrong now?

---

### Post by hyperair on 2007-07-08
You're using nVidia. This is a bug in the nVidia drivers. When the memory on your video card has been depleted, the new windows that appear are black. You need to minimize a few windows or something of that sort, and then reopen it. Or make it smaller until it stops being black.

---

### Post by benhagerty on 2007-07-08
So there is nothing I can do, stupid nVidia

---

### Post by hyperair on 2007-07-08
Well of course there's the option of disabling Blur and reflection if you have those on, and also diasbling group/tab windows, as well as upgrading your graphics card.

There's also a fix for nVidia cards black windows, but I forgot where I saw it, and never tried it because I hardly ever ran into that bug.


EDIT: I found it!! [http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window](http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window)

---

### Post by benhagerty on 2007-07-08
I wish I could upgrade my graphics card but I have a laptop and it is 2 years old and I am getting ready to get a new one luckily

---

### Post by muggins on 2007-12-31
> **hyperair said:**
> Make sure you have this line:
```

Option "AddARGBGLXVisuals" "True"

``` in your "screen" section.

I had the same problems after a recent upgrade to gutsy. The above code solved my problems with a blank terminal and no exit + minimize buttons in firefox.

---

### Post by hyperair on 2007-12-31
Keep in mind that this fix is only for nVidia drivers. Specifically the legacy drivers. The newest drivers do not need that.

---

