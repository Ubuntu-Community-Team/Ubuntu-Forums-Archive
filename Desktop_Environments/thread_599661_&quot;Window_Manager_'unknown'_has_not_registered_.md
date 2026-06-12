---
title: "&quot;Window Manager 'unknown' has not registered a configuration tool&quot;"
date: 2007-11-01
forum: Desktop Environments
---

### Post by akkim on 2007-11-01
All,
i just successfully upgraded Xubuntu to 7.10 and installed Gnome additionally to Xfce by "apt-get install gnome-desktop-environment". All went fine.

When i then login using Gnome and open the first application like firefox or whatever, the application window is not displayed completely. Upper menu and bar are missing. If i want to configure windows and behaviour the rror message

"Window Manager 'unknown' has not registered any configuration tool"

I guess Gnome is not registered right somewhere.

Any ideas?


Thanks a lot,
Akkim.

---

### Post by rmtzr on 2007-11-03
Try this:

1. In Terminal, run metacity (the gnome wndows manager); the full windows are restored

2. In Preferences / Sesions  /Session Options check "Automatically remember running applications..."

3. Log off and Log in

---

### Post by craigmjackson on 2007-11-20
Seems like this is directly related to Metacity itself.  The session profiles for each Metacity user are in ~/.metacity/sessions/<session id>.  I deleted all the files in this directory and the issue was resolved.  I will repost if I see this again, and will check out the contents of these session files more closely.

Craig Jackson
[email]craigmjackson@gmail.com[/email]

---

