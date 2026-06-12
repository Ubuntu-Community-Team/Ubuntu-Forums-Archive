---
title: "My GDM login shows 1/4 screen"
date: 2009-04-27
forum: General Help
---

### Post by Dragonbite on 2009-04-27
First off, I like the login screen image for Jaunty.  I liked it when I first saw it.

Then my son got on the computer and he was taken aback by everything changing on him and complained about everything being so small. So I changed the resolution for him to something smaller (1440x900? I don't remember but ti's widescreen).

Now when I go to the login screen it is zoomed to the login dialog box to put my username and password, but the logo on the lower right is not visible and neither are the menu choices on the bottom left. I can get those choices by hitting F10, but I want to see the entire screen and not the login box.

Can anybody help me!?!  I don't see anything in #dmesg!

---

### Post by Dragonbite on 2009-05-19
bump.

I really dislike not seeing the menu on the bottom.

Where is the configuration file that tells the system what resolution to display the login screen (GDM?)

---

### Post by timcredible on 2009-05-19
put the resolution back to the native resolution.  if the fonts are too small, make them larger by system->appearance->fonts.

---

### Post by Legace on 2009-05-19
Make sure the root resolution is same as your resolution.
I think you could do it like:

```
sudo -i
gnome-display-properties
```

If that doesn't work, log in as root from GDM and then change.

---

