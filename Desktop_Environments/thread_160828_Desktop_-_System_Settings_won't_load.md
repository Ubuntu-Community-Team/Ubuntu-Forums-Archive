---
title: "Desktop - System Settings won't load"
date: 2006-04-15
forum: Desktop Environments
---

### Post by firecrotch on 2006-04-15
Hello.

I recently tried to set up my background to display a web page through the System Settings Desktop settings (never got it to work) and now, I cannot get into the desktop settings to change anything.  When I attempt to get into it, it just stops responding.  Does anyone know what the problem might be or how to fix it?  It would be greatly appreciated, thanks!

EDIT: I should also add that all of my desktop icons have disappeared, and I cannot right click on the desktop at all.

---

### Post by aysiu on 2006-04-15
Try this.

1. Press Control-Alt-F1
2. Log in
3. Type ```
mv ~/.kde ~/.kde_old_and_messed_up
4. Log out
5. Press Control-Alt-F7
6. Press Control-Alt-Backspace
7. Log in again (if you somehow end up at the console, type [code]sudo /etc/init.d/kdm restart
```)

---

### Post by firecrotch on 2006-04-15
Thanks a lot! That solved the entire problem.   Just wondering though - what exactly did doing that do?

---

### Post by fdoving on 2006-04-16
That did move all your KDE settings to a backup folder, and let you start from the defaults.

- Frode

---

