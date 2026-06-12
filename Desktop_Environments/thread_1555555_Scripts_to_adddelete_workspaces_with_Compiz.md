---
title: "Scripts to add/delete workspaces with Compiz"
date: 2010-08-18
forum: Desktop Environments
---

### Post by deafiant on 2010-08-18
I was reading an article in Australian PC magazine that mentioned Gnome Shell in the upcoming Gnome 3.0. Gnome Shell will have a 'Overview' mode with large '+' and '-' buttons to add or delete additional workspaces. I was wondering if I could do something similar with Compiz.

A bit of goggling & experimenting and I found out I can - using the dbus plug-in! No big buttons but I have hot-key goodness. The script to add a workspace is:

```
#!/bin/bash
ws=$(dbus-send --print-reply --type=method_call \
--dest=org.freedesktop.compiz  /org/freedesktop/compiz/core/screen0/hsize \
org.freedesktop.compiz.get | tail -c -2)

dbus-send --type=method_call --dest=org.freedesktop.compiz \
/org/freedesktop/compiz/core/screen0/hsize \
org.freedesktop.compiz.set int32:$[ $ws + 1 ]

```

Quick explanation - We tell dbus to get the horizontal virtual size and tail grabs just the number that we are after. This is saved in the variable ws. Then we add 1 to ws and tell dbus to set the new horizontal virtual size.
(Note that I am new to Ubuntu and bash - there may be better ways of doing this. And it could be made more robust with error-checking.)

I saved this script as 'addWorkspace' and bound it to <Control><Alt>equals. The second script that I saved as 'delWorkspace' and bound to <Control><Alt>minus is exactly the same except for the last bit - we need to take away instead of add.

```
#!/bin/bash
ws=$(dbus-send --print-reply --type=method_call \
--dest=org.freedesktop.compiz  /org/freedesktop/compiz/core/screen0/hsize \
org.freedesktop.compiz.get | tail -c -2)

dbus-send --type=method_call --dest=org.freedesktop.compiz \
/org/freedesktop/compiz/core/screen0/hsize \
org.freedesktop.compiz.set int32:$[ $ws - 1 ]

```

Hope this helps someone else. It is a lot of fun when using Expo to quickly add or drop another workspace.

---

### Post by Bonster on 2010-08-18
Great Script!!
I notice it only adds it Horizontally how do you make it add Vertically?

---

### Post by deafiant on 2010-08-19
Bonster & aryy113, thanks for the praise. I am glad that others can make use of my little bit of tinkering. Even [Webupd8 has written a post about it]("http://www.webupd8.org/2010/08/how-to-add-delete-workspaces-in-compiz.html")! Wow! There is a more efficient script in the comments so it is worth while checking out.

> how do you make it add Vertically?
Change all occurences of ```
/org/freedesktop/compiz/core/screen0/**hsize**
``` to ```
/org/freedesktop/compiz/core/screen0/**vsize**
```

---

### Post by nilarimogard on 2010-08-19
I updated the [post]("http://www.webupd8.org/2010/08/how-to-add-delete-workspaces-in-compiz.html") with the simplified version by Anno Nymus. It doesn't really matter how the code looks as long as it works the same, but it looks prettier now :D

Thanks once again for the script!

---

