---
title: "Cannot disable startup applications"
date: 2011-05-13
forum: Desktop Environments
---

### Post by Gerald here on 2011-05-13
Hello.

   I am wondering how to disable startup applications in GNOME 2.30.2 running on Ubuntu 10.04 LTS (64-bit). 
When I open Startup Applications (System --> Preferences -->) and uncheck a startup program, close Startup Applications and open it again, the program I unchecked is checked again. Even if I remove a program from the list it's there again the next time I open Startup Applications and the program opens when I restart. I guess this is a bug !? Any ideas ?

---

### Post by Gerald here on 2011-05-25
Now I found out why it didn't work. Some program might have changed the permissions of my [home]/.config/autostart folder as the command ```
gnome-session-properties
``` gave me a "Could not write [...]" error message. After changing the permissions for this folder Startup Applications works again.

---

