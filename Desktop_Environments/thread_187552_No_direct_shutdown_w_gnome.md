---
title: "No direct shutdown w/ gnome?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by roots on 2006-06-03
hi there,

some people already wrote about that kind of issue --- using the power button on my laptop does not switch my computer off directly anymore, that is - without having to go through the quit dialog window!

i already used gconf-editor to set the following entry in

```
/apps/gnome-power-manager/action_power_button
```

from "*interactive*" to "*shutdown*"

but still i get the dialog when pressing the power button.


is there any solution for this yet? i find it quite annoying to have to use the dialog or shutdown -h now evertime i just want a quick "off"...


cheers,
roots

---

### Post by roots on 2006-06-03
ok, my mistake: the gnome settings have to be changed as "user" not using "sudo"...

now shutdown via button works again!


cheers,
roots

---

