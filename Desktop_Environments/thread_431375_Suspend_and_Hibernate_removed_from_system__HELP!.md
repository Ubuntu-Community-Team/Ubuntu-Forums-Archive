---
title: "Suspend and Hibernate removed from system?  HELP!"
date: 2007-05-03
forum: Desktop Environments
---

### Post by naked on 2007-05-03
I just did a fresh install of Feisty, and then decided I'd like to the Ubuntu CE.  So I ran the convert script, and now I'm missing my suspend and hibernate options from everything.  Deskbar doesn't show them as actions, the shutdown menu doesn't list them, gnome-power-manager doesn't have them as options in settings on upon right-click.  I reinstalled everything I can think of that is acpi/suspend related.  And as far as I can tell, CE wouldn't actually effect anything related to this.  All it did was install other programs.

Any help in investigating this problem would be helpful.  Being able to suspend my laptop is a very important issue to me!

I have a Dell 700m, but have never had this issue before, so I don't think its dell specific.  I had another install of Feisty on this same computer and didn't have this issue.

L

---

### Post by scanez on 2007-05-03
Run gconf-editor, go to apps --> gnome-power-manager, and make sure "can_suspend" and "can_hibernate" are checked.

---

