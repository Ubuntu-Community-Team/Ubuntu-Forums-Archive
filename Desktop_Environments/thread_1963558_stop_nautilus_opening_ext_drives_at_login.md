---
title: "stop nautilus opening ext drives at login"
date: 2012-04-22
forum: Desktop Environments
---

### Post by ng201 on 2012-04-22
Having such trouble finding how to stop this in Ubuntu 11.10. Nothing I google gives a working answer.

When I log in Nautilus soon opens windows for both partitions on my external drive. Usually over what I've just opened.

dconf-editor seems no help: No nautilus under apps. No relevant options under org.gnome.nautilus

"gsettings list-recursively org.gnome.nautilus" doesn't show anything I need either.

What should I do?

---

### Post by sparhawkthesecond on 2012-05-08
I'm not sure, but is [this](https://help.ubuntu.com/community/Mount/USB#Configuring_Automounting) useful?

---

### Post by sparhawkthesecond on 2012-05-08
Or [this](http://ubuntuforums.org/showpost.php?p=8078159&postcount=2)? But perhaps not, as this will prevent ALL mounted drives from automatically opening a window. I'm not sure how to do it for specific drives only.

---

