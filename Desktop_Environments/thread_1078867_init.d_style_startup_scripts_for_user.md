---
title: "init.d style startup scripts for user"
date: 2009-02-23
forum: Desktop Environments
---

### Post by librano on 2009-02-23
I was just wondering if there is a default or standard location where one could have init.d style scripts that are run on user login... The actual scripts could be in the system folders but with links in the user's home directory.

I am thinking of something like the way X has it's own scripts in /etc/X11/Xsession.d/

I do not want to use a Gnome/XFCE/KDE specific method to do this. Standard is good ;)

---

### Post by snova on 2009-02-23
**~/.config/autostart**

Though I don't think they can be scripts, but .desktop files... well, I suppose you could create some stubs:

```

[Desktop Entry]
Exec=/path/to/login-script.sh

```

---

