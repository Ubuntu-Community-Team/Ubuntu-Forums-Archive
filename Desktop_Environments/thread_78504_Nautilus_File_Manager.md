---
title: "Nautilus File Manager"
date: 2005-10-18
forum: Desktop Environments
---

### Post by kreso on 2005-10-18
1) Is there an alternative to nautilus? (I don't want konqueror either :P)

2) Can I replace those location buttons with a simple textbox in the nautilus browser so I can copy paste the location ("/usr/lib/...")

3) Can I launch a terminal that starts from the current location I am in nautilus, like when you press F4 in konqueror?

---

### Post by Stormy Eyes on 2005-10-18
[QUOTE=kreso]1) Is there an alternative to nautilus? (I don't want konqueror either :P)[/quote]

There are lots of alternatives. Some people like ROX-filer (**sudo apt-get install rox-filer**), and others like GNOME Commander (**sudo apt-get install gnome-commander**). I favor bash, myself. *cheeky grin*

[QUOTE=kreso]2) Can I replace those location buttons with a simple textbox in the nautilus browser so I can copy paste the location ("/usr/lib/...")[/quote]

No, but the menu in browser mode has an "Open Location" option. Have you tried that?

[QUOTE=kreso]3) Can I launch a terminal that starts from the current location I am in nautilus, like when you press F4 in konqueror?[/QUOTE]

There's a package you can install to add an "Open in Terminal" command to Nautilus' right-click menu. Try **sudo apt-get install nautilus-open-terminal**.

---

### Post by flaming_monkey on 2005-10-18
1. If you want to use File Commander, be my guest but I'd stick with Nautilus.

2. goto Applications > System Tools > Configuration Editor

then navigate to apps > nautilus > preferences

and check "always_use_location_entry" and make sure "start_with_location_bar" is also checked.

3. System > Preferences > Keyboard Shortcuts and then assign a key to "Launch Terminal"

Hope that helps.

---

### Post by Joe_lurker on 2005-10-18
You can change the default file browser window to have the location shown.  Clock on Applications | System Tools | Configuration Editor.  In Configuration Editor navigate to Apps | nautilus | preferences.  Check the box always_use_location_entry.  Alternativly you can type in the file window and hit enter when you get to the file/folder you want.

As far as a terminal I don't know the answer to that.  I always have a terminal open anyhow.  That's how I usually work.

Joe

Sorry, I didn't see the replay already posted.

---

