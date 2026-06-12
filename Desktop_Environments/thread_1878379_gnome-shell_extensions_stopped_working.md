---
title: "gnome-shell extensions stopped working"
date: 2011-11-09
forum: Desktop Environments
---

### Post by lime4x4 on 2011-11-09
I can no longer enable gnome-shell extensions The only one i can turn on or off is the theme one. This was working the other week. I'm using ricotz ppa for gnome shell. I've tried removing gnome-shell and reinstalling and still does the same thing

---

### Post by cbowman57 on 2011-11-09
When you pull up the errors in looking glass (alt+f2 lg enter) what does it tell you about those extensions?

---

### Post by lime4x4 on 2011-11-09
extension is not compatible with current gnome-shell

---

### Post by cbowman57 on 2011-11-09
Ok, that likely means that your extensions weren't made for your shell version.

But, if they were & still not working than you need to match the version in the metadata.json to the shell you are using.

Did you recently upgrade or dist-upgrade?

---

