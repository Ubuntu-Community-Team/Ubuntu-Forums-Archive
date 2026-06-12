---
title: "Beryl crashes upon Cube rotation"
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by 213374U on 2007-06-18
Beryl works perfectly until I try to rotate the cube and then crashes as soon as I snap to a workspace. Also when I rotate the cube, only the face that I am rotating from has a background... the other three sides only contain my top and bottom taskbars. What's going on and how can I fix this?

---

### Post by zero244 on 2007-06-18
That is strange.......I do know if you muck around with the timing settings for the cube you can screw things up......you could delete the settings ini file for beryl and restart it. All the settings go back to the default or most of them do.
You may have to turn the cube off.

---

### Post by EagleRock on 2007-06-18
I had the desktop issue myself the other day.  You need to make sure the "My Window Manager Supports Multiple Desktops" is not checked, otherwise you will not get backgrounds on those three sides of the cube.  I'd give you the exact place of the settings, but I don't have that PC with me right now.

If no one responds by the time I get home (or if you can't find it), I'll be glad to find the exact location of the setting for you.

---

### Post by 213374U on 2007-06-18
I'll try to find the "My Window Manager Supports Multiple Desktops" setting, if I can't or it doesnt work, I'll try deleting the settings.ini file and post up my results. Thanks

---

### Post by 213374U on 2007-06-18
Couldn't find "My Window Manager Supports Multiple Desktops" but I did find "My Window Manager Supports Multiple Viewports" and disabled that.... still crashes. 

Now before I go deleting files, which settings file exactly do I need to delete? Or is there a button that I can press to reset Beryl to default settings?

---

### Post by EagleRock on 2007-06-18
The "My Window Manager Supports Multiple Viewports" is the one I meant.  I don't know if you tried rebooting or Ctrl + Alt + Bksp to see if it works.  You might also want to attempt selecting Metacity as your manager, then switching back to Beryl to see if the crash occurs.  Other than that, your personal config file is in your home directory.  I don't remember the exact name, but it is a hidden file.  If you type "ls -l ~", you'll see a bunch of hidden files in your home directory, including a beryl file.  I don't know if you can delete it, though, as I never tried.  

I'd try renaming the file to see if it gets recreated automatically.  Again, I forget the name of the file, but let's assume it's called .beryl-settings or something like that.  If you type "mv .beryl-settings .beryl-settings.old", you can then reboot and see if your settings are reset.  Otherwise, I'm kinda out of ideas...

---

### Post by 213374U on 2007-06-18
Okay, got the cube working without deleting that file. But now I've lost my window borders... what happened?

---

### Post by avik on 2007-06-18
Run emerald, which is the window decorator that comes with Beryl.

---

### Post by zero244 on 2007-06-18
Are you talking about the Title bars at the top where the close, max, minimize buttons are.
Check and make sure Window Decorations is checked. If it is checked you will need to add this to your Xorg.conf file.
Place it in the "Screen section" just above the DefaultDepth line.

Option "AddARGBGLXVisuals" "True"

Also if you want to get the default settings back you can delete the Settings file in your ./beryl folder. It will be replaced the next time you load Beryl. You might have to delete it while beryl is turned off.

---

### Post by 213374U on 2007-06-18
Okay, now when I try to load beryl by clicking the jewel in the top task bar and Select Window Manager>Beryl, the screen goes black and stays that way. I did exactly what zero244 recommended and still the black screen.

Also, when I enter 

```
top
```

Emerald is using 96-97% CPU... it's frozen.

---

