---
title: "Editing GRUB Menu"
date: 2009-05-04
forum: General Help
---

### Post by user 123 on 2009-05-04
I am using this guide to try to speed up Jaunty

[http://www.goitexpert.com/entry.cfm?entry=ubuntuguide](http://www.goitexpert.com/entry.cfm?entry=ubuntuguide)

one of the instructions says:

Boot Profile

You have just made a lot of changes to your system. Re profiling your boot will reorganize it and make it faster on boots afterwards.

    * Reboot your PC.
    * When you come to your grub list, hit escape to see your grub menu.
    * Edit the topmost line and add the word below to the end of it.

profile

    * Then just reboot the system.



However the escape key does nothing in the grub list (which i'm taking to be the list of kernels on boot).

Am I doing something wrong here?

Thanks

---

### Post by snowpine on 2009-05-04
Press 'e' to edit the top line.

'Esc' would only be necessary on a system where the GRUB menu is hidden by default. (Doesn't sound like yours is hidden, so you can skip that step.)

---

