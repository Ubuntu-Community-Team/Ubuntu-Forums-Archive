---
title: "Media keys + Certain Shortcuts Disabled"
date: 2009-04-05
forum: General Help
---

### Post by SnoFox on 2009-04-05
Honestly, this has annoyed me to the point of reinstallation.
My media keys (Play/Pause, Stop, Fast forward, Rewind), any other "extra" keys on my keyboard, and certain shortcuts (Ctrl+Alt+L) have been disabled by something.

I think it was by x11vnc, but anyway, how can I get these re-enabled?
They're all listed in System -> Preferences -> Keyboard Shortcuts (GNOME), and they're being detected by -some- programs as being pressed, but have no effect.
For example, in the Keyboard Shortcuts applet, it detects "Play/Pause" being pressed. In Audacious, it doesn't detect detect the key being pressed, unless I use a modifier key with it. `xev` detects everything (I care about) being pressed, correct keycode and all.
I'm thinking this is an X-level problem, because it affects both GNOME and KDE (I installed and considered switching to KDE fully just because of this problem.) Also, Ubuntu Intrepid Ibex has been running perfectly for the past two weeks, until something last week triggered this.

Please help, I'm getting desperate. :( And I don't want to install Windows, and reinstalling Ibex fully is a last resort option, as I'll have many, many things to reconfigure, and start over.

---

### Post by SnoFox on 2009-04-05
Bump.
Come on, I could use ANYTHING, really. A config file, a man-page, a file path, even. Just don't ignore me like every other support place. I tried resolving this myself to no avail, so I turn to you for help. I don't want to just be ignored.

---

### Post by agnes on 2009-04-19
I'm not an expert on this, but I have some suggestions which may be useful:

**1.** System->Preferences->Keyboard; tab: Layouts.
Select layout, and click on "Apply System-wide".

**2.** Try it with the program **XKeyCaps** (needs to be installed first).

**3.** Try it with **gconf-editor**.

**4.** There are some plugins available for Audacious which can handle key bindings. So install those (via Synaptic, search for "audacious plugin").

By the way... I've seen a lot of posts on the Ubuntu forums regarding problems with keys not working. (With Intrepid.) I'm also having some problem with one key. Apparently keycodes and -bindings are a problematic issue for many users. So perhaps that's why you didn't get any reply.

---

### Post by SnoFox on 2009-04-25
None of those seemed to have worked. **gconf-editor** would probably have fixed it, but I couldn't find the bit to change. I just nuked all my GNOME and Nautilus configuration files and that seemed to have fixed it.

---

