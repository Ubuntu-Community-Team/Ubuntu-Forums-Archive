---
title: "Touchpad functionality incomplete AND malfunctions"
date: 2017-04-12
forum: Desktop Environments
---

### Post by Antoon Stessels on 2017-04-12
I've had this problem before in Ubuntu 16.10, and now in Ubuntu GNOME 17.04 Final Beta:

In 'Mouse & Touchpad' Settings, I can't select 'tap to click' or 'two-finger scrollings' options. They're just not there.
This invisibility of these options only pertain to GNOME and GNOME Classic.
Everything does work under Wayland!

Furthermore, when I resort to de Dconf Editor,
all options are visible, BUT ...

... switching 'Natural Scrolling' on/off doesn't change the behaviour of the Touchpad.

Again, under Wayland, it does work.

Does anyone have a solution for this, apart from re-installing Ubuntu GNOME from scratch?

Thanks in advance.

---

### Post by Antoon Stessels on 2017-04-12
I found the answer myself ...

When upgrading, or switching between DEs, the update manager could be installing both libinput and synaptics.

This can result in a conflict.

Deleting synaptics is easiest, since there are no dependencies. So, deleting this in Synaptic solves the issue.

---

### Post by tranvannhancu on 2017-08-30
I have the same issue here. Can you post your solution?

---

