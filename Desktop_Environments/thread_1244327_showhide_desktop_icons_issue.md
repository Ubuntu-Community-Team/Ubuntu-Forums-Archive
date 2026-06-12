---
title: "show/hide desktop icons issue"
date: 2009-08-19
forum: Desktop Environments
---

### Post by RobHK on 2009-08-19
I used the following script (found at [http://www.ivy.fr/blog/index.php/2008/05/08/85-from-macos-to-ubuntu-show-hide-desktop-icons-on-gnome](http://www.ivy.fr/blog/index.php/2008/05/08/85-from-macos-to-ubuntu-show-hide-desktop-icons-on-gnome)), linked to a panel launcher, to be able to show/hide the desktop icons with a click:

```
#!/bin/bash
if ( `gconftool --get /apps/nautilus/preferences/show_desktop` == "true" ) then
gconftool --set /apps/nautilus/preferences/show_desktop \
--type boolean false
else
gconftool --set /apps/nautilus/preferences/show_desktop \
--type boolean true
fi
# EOF

```

It worked fine the first few times, hiding the icons when clicked and restoring them (with a second or two delay) when clicked again, but on one attempt it hid the icons but did not restore them. This is still the case.

I checked in gconf-editor (/apps/nautilus/preferences/show_desktop), and the script is doing what it is supposed to do, i.e. check or uncheck the Show Desktop box, but the icons do not reappear when it is checked.

Provided the box is in checked state when I log out, the icons will be back on the desktop when I log in again. I can hide them, but not restore them, even by checking the box manually.

So the issue is not in the script, but in the functioning of the show desktop checkbox feature.

---

### Post by mcduck on 2009-08-19
You could try restarting Nautilus after enabling the desktop icons again.

Or actually killing Nautilus, as it will respawn automatically..

```

#!/bin/bash
if ( `gconftool --get /apps/nautilus/preferences/show_desktop` == "true" ) then
gconftool --set /apps/nautilus/preferences/show_desktop \
--type boolean false
else
gconftool --set /apps/nautilus/preferences/show_desktop \
--type boolean true
killall  nautilus
fi
# EOF
```

---

### Post by RobHK on 2009-08-19
> **mcduck said:**
> You could try restarting Nautilus after enabling the desktop icons again.

Or actually killing Nautilus, as it will respawn automatically..

```

#!/bin/bash
if ( `gconftool --get /apps/nautilus/preferences/show_desktop` == "true" ) then
gconftool --set /apps/nautilus/preferences/show_desktop \
--type boolean false
else
gconftool --set /apps/nautilus/preferences/show_desktop \
--type boolean true
killall  nautilus
fi
# EOF
```

Running your script doesn't do anything. Restarting Nautilus from a terminal just opens a Nautilus window. But no icons.

What puzzles me is that it worked, initially.

---

### Post by RobHK on 2009-08-21
> **mcduck said:**
> You could try restarting Nautilus after enabling the desktop icons again.

Or actually killing Nautilus, as it will respawn automatically..

```

#!/bin/bash
if ( `gconftool --get /apps/nautilus/preferences/show_desktop` == "true" ) then
gconftool --set /apps/nautilus/preferences/show_desktop \
--type boolean false
else
gconftool --set /apps/nautilus/preferences/show_desktop \
--type boolean true
killall  nautilus
fi
# EOF
```

Got it. Restarting Nautilus does do the trick, only when I did from a terminal closing the terminal lost the icons again.

Using your suggestion but with "nautilus" instead of "killall nautilus" works.

---

### Post by RobHK on 2009-08-21
Just one minor issue remaining: 

The "nautilus" command opens my home directory in Nautilus. While this is no big problem it is not the desired behaviour.

What command can I send to kill that window without ending Nautilus (and having my icons disappear again)?

Alternatively: is there a command which would bring back the icons without opening the window?

---

