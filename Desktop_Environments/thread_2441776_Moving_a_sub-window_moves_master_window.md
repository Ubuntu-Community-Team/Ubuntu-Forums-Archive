---
title: "Moving a sub-window moves master window?"
date: 2020-04-26
forum: Desktop Environments
---

### Post by bellbotanics on 2020-04-26
Upgraded to 18, and now when trying to move a pop-up window (sub-window) in Libre Office it moves the master window (both pop-up and parent).

Testing in other programs indicate it's likely something with Libre Office, for other software (GIMP + Android Studio) behave normally.

**Edit:** Sorry found answer, but don't know how to delete.
[B]
Answer:[/B]
gsettings set org.gnome.mutter attach-modal-dialogs false

OR

gsettings set org.gnome.shell.overrides attach-modal-dialogs false


[https://askubuntu.com/questions/972276/how-do-i-move-child-windows-without-moving-or-minimizing-parent-in-gnome-3](https://askubuntu.com/questions/972276/how-do-i-move-child-windows-without-moving-or-minimizing-parent-in-gnome-3)

---

