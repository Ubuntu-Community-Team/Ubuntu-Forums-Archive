---
title: "One Keypress in Multiple Windows?"
date: 2011-03-27
forum: Desktop Environments
---

### Post by zone z5 on 2011-03-27
OK, take the following situation:
   I have multiple windows open. I select one window, and press a key. This causes something to occur in said window. This keypress only works for the one window I have selected. I would like this keypress to work for all the windows open on my desktop, which total to 9.

---

### Post by zone z5 on 2011-03-28
It's been almost 24 hours, with no response.
Bump.

---

### Post by zone z5 on 2011-04-02
It has been several days now, with no response.
Bump.

---

### Post by Copper Bezel on 2011-04-02
There's no easy way to do this, and without knowing the problem you're trying to solve, it's a bit difficult to understand the rationale. You'd have to create a script and probably make use of a pair of packages called wmctrl and xdotool - look into those to get started. It would involve fetching a list of open windows, then carrying out the keystroke while focusing each one in sequence.

Seriously, though, what exactly are you trying to *do*? There's probably a much simpler solution than actually sending a keystroke to all of your open windows.

---

### Post by kio_http on 2011-04-02
Well, technically KDE's UI (like most other UI's Mac OS, Windows etc) is designed so that the active window accepts keystrokes except for services and service-like applications like music players. I doubt it would be easy to do this without modifying the source code of the applications you want to capture the keystrokes.

Any chance of getting an insight on what you are trying to do?

---

