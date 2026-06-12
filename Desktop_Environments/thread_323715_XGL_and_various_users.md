---
title: "XGL and various users"
date: 2006-12-22
forum: Desktop Environments
---

### Post by benjaminwr on 2006-12-22
Hi,
I am having a strange problem, I have XGL and Beryl running fine with my normal user... but when I set up another user on the system and try to log in I get an error message saying that my session lasted less than 10 seconds, and it has to end.

I cannot log in to the other users account using XGL, i can only use normal Gnome session.

Any ideas??

---

### Post by penguins! on 2007-06-02
Just want to bump this one as I'm having the same problem and still haven't found a solution.

XGL works fine on the primary user account but when I log out and attempt to log into another account with an XGL session I get the same error reporting that the X session only lasted 10 seconds and stating that /tmp/.X1-lock couldn't be removed.

Found an [old thread]("http://ubuntuforums.org/showthread.php?t=211029") that suggests installing XGL as the primary X server is a workaround but I'd really like to be able to keep the current XGL-as-a-session setup as fglrx, XGL and Beryl isn't the most stable combination in the world.

Any ideas?

---

### Post by kellemes on 2007-06-02
I'm not into Beryl so I'm only guessing..
It seems like a permission issue so maybe you should see to it the user is a member of the right groups? Maybe you should experiment a littlebit to find the group(s) the Beryl-user has to be a member of.

---

### Post by nikogawa on 2007-06-02
The following worked for me:
```

sudo gedit /etc/gdm/PostSession/Default

```
then add the following lines just before the line "gdmwhich () {"
```

rm -f /tmp/.X1-lock
rm -f /tmp/.X11-unix/X1

```

---

### Post by khughitt on 2007-06-03
I was having the same problem, and the above solution worked for me as well- thanks! :)

Does anyone know if this has been reported to bug-tracking?

---

