---
title: "Activating Changes to Unity Launchers"
date: 2013-05-06
forum: Desktop Environments
---

### Post by apollothethird on 2013-05-06
You can create a Unity launcher with gedit and placing the desktop file in ~/.local/shared/applications.  This is great.  However, I find that if I have to make changes such as the Icon image or item's name, it won't take effect unless I log out of X and log back in.

Logging in and out is very cumbersome when I have a number of project open that I have to close then restart and figure out where I left off.

Does anyone know of a way to flush the buffer so that the changes can take affect without having to log  on and log back in?

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by mcduck on 2013-05-06
simply restarting Unity should do the trick. Hit Alt-F2 and run this:
```

unity --replace
```

---

