---
title: "Gnome cube vanishes?"
date: 2007-07-13
forum: Desktop Effects &amp; Customization
---

### Post by Hybrid86 on 2007-07-13
I am new to ubuntu and just enabled desktop effects. Everything was working fine at first. However, after freezing up when I tried to put it in suspend, the cube no longer worked; it only showed one workspace as existing at the bottom right :confused:

Confused, I tried to restart, but it came back the same! The effects are still enabled, the cube's just not there anymore! I even tried manually adding extra workspaces, but the cube feature is just gone. I'm sure this is probably an easy fix, but right now I'm in the dark.
Any solutions?

---

### Post by hyperair on 2007-07-13
Go to Applications->System->Configuration Editor. Navigate to the key /apps/compiz/screen0/options and in the right panel look for hsize. Make sure that the value for it is 4.

---

### Post by bdtgp on 2007-07-13
That is much too confusing for some.  Its in General Options in the Compiz Manager.  Go to desktop size.  Site horizontal to 4 and youre done.  Nothing in the terminal.

---

### Post by hyperair on 2007-07-14
I never mentioned anything about the terminal did I? =P

Besides, not many people have this so called Compiz Manager. In fact I don't even know what you're talking about, and I've used Beryl, Compiz and Compiz Fusion before, currently using Compiz Fusion. I've only seen a configuration tool for the regular Compiz which is called Compiz Settings Manager (and that was manually installed from Trevino's repository), and the GL Desktop (also manually installed but from the universe repository) settings but that's obviously not what you were talking about.

---

### Post by eternaldeals on 2007-07-14
I'm having the same problem when I started desktop effects everything worked good but after 10 min the cube stop working. I'm running ubuntu 7.04 and so far all of these post make no scents to me. please help

---

