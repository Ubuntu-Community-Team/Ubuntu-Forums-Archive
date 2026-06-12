---
title: "Missing gconf-editor options"
date: 2011-01-29
forum: Desktop Environments
---

### Post by aaaa1 on 2011-01-29
I was trying to make Gnome display the date in a better format. I tried using gconf-editor as described in the thread at [http://www1.ubuntuforums.org/showthread.php?p=9095307](http://www1.ubuntuforums.org/showthread.php?p=9095307), but I also found that apps > panel> default_setup > applets > clock had no prefs item.

Unfortunately, the solution which worked for quixote (stop running as root) didn't help me as I was running as the only account I've set up on the system, and all of the files in ~/.gconf are owned by that user.

Does anyone know what else could cause options to vanish like that? I'm running Gnome 2.32.0. Thanks.

---

### Post by gmargo on 2011-01-29
The **custom_format** option only shows up in the instantiated clock applet preferences. 

Open the gconf-editor and navigate to **/apps/panel/applets/clock_screen0/prefs**.  

Here you can set the "custom_format" string.  Also change the "format" value to "custom".  I just tested it using "%H:%M:%S" as the custom_format.  I had to enable "show_seconds" to get the time to update every second.

---

### Post by aaaa1 on 2011-01-29
> **gmargo said:**
> The **custom_format** option only shows up in the instantiated clock applet preferences. 

Open the gconf-editor and navigate to **/apps/panel/applets/clock_screen0/prefs**.
There is no /apps/panel/applets when I open gconf-editor, only default_setup, general and global.

---

### Post by gmargo on 2011-01-29
Are you running the gnome clock applet?  Or perhaps something else?

---

### Post by aaaa1 on 2011-01-29
> **gmargo said:**
> Are you running the gnome clock applet?  Or perhaps something else?
I have the clock on the top panel which came with Ubuntu, which is more or less as described in gnome-help except that it doesn't have a preferences option.

---

### Post by Krytarik on 2011-01-30
I hope you don't launch gconf-editor as root! Just press Alt+F2 and enter "gconf-editor".

---

### Post by aaaa1 on 2011-01-30
> **Krytarik said:**
> I hope you don't launch gconf-editor as root! Just press Alt+F2 and enter "gconf-editor".
Should I be worried that Alt+F2 does nothing?
In actual fact, I've been running gconf-editor from a terminal window (which was either started from the "applications" thing or from another screen with xterm -display :0) using the command "gconf-editor" (or /usr/bin/gconf-editor, I suppose).

---

### Post by Krytarik on 2011-01-30
But you do Gnome and Gnome Panels running? Right-click at one of your panels, then at "About". Or are you actually running Unity/Netbook Edition?

---

### Post by aaaa1 on 2011-01-30
> **Krytarik said:**
> But you do Gnome and Gnome Panels running? Right-click at one of your panels, then at "About". Or are you actually running Unity/Netbook Edition?
Sorry, I realise that it was. I've switched to the "desktop" interface and more stuff now works. Thanks for your assistance.

---

### Post by poisonborz on 2011-10-08
because this thread turns up in google prominently for the problem, here is another possible error:
one must run gconf-editor **without sudo**, otherwise the desired pref keys will not appear.

---

### Post by Krytarik on 2011-10-08
> **poisonborz said:**
> here is another possible error:
one must run gconf-editor **without sudo**, otherwise the desired pref keys will not appear.
Yeah, as I already pointed to in post #6. ;-)

---

