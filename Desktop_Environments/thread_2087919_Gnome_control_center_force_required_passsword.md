---
title: "Gnome control center force required passsword"
date: 2012-11-25
forum: Desktop Environments
---

### Post by nerolokki on 2012-11-25
Hello,
I need to restrict access to gnome-control-center to admin only.
It can do so that it works from terminal?

thanks

---

### Post by Frogs Hair on 2012-11-25
Hello nerolokki,

I thought this would be simple from the main menu by adding a gksu command to the launcher properties. The problem is there is no way to add the command in to the gnome-control-center / system settings in launcher properties as with other applications.The command also could be accessed and changed  


The best I was able to do is hide the gnome-control-center / system settings and start it from the terminal , but this requires no password. The main menu will only hide items in a Gnome desktop environment and anything installed is available to Unity dash. Even the guest account has access to system settings though it doesn't save settings after logout.

---

### Post by nerolokki on 2012-11-26
Thank you for your answer.
I temporarily solved by changing the rights of / usr / bin / gnome-control-center to 700

If I do not want some users to use some software, the only way is to act on the permissions users and groups.

But it is so strange that Linux does not offer this option.

---

