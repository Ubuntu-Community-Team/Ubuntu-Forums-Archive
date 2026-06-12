---
title: "KDE 4.13 - OpenGL screensaver doesn't display at the foreground anymore"
date: 2016-02-15
forum: Desktop Environments
---

### Post by pubalapoub on 2016-02-15
Hi all,

as I've just found the cause to my issue, I'd like to share it with you, in case some of you would face it as well.

One day I noticed that upon entering the screenlocking mode, my OpenGL screensaver stopped displaying at the foreground. Instead, the KDE login screen was displaying (allowing me to enter my password to unlock the screenlocker and get back to my KDE session).

Additional symptoms:

- what I would call the "keyboard focus" wasn't set to the password field. Each time I had to press any of my keyboard keys **once** before the focus went to the password field (then I could type in my password normally).

- when pressing Enter after my password, I could see the OpenGL screensaver display very shortly before getting back to my KDE desktop. Which made me understand the screensaver was running fine, but not displaying at the foreground as it used to.

Today at last I could find a KDE option that, when disabled, would solve my issue.

Go to:

- KDE system configuration
- Desktop Effects
- Advanced Options tab
- **Disable** option "**Suspend desktop effects for fullscreen windows**"
- Click the "Apply" button

Not sure of the consequence of _allowing_ desktop effects for fullscreen windows, but at least does it allow the screensaver to display normally again. At the foreground :D

---

