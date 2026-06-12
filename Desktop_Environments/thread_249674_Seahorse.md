---
title: "Seahorse"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Ziggy72 on 2006-09-02
I've just updated Seahorse using Synaptic Package Manager to v.0.9.3. However, on every reboot I now get the message "Could not load icon" "Seahorse-key.png not found". But, in fact, Seahorse-key.png does exist and I've even replaced the file thinking that it may be corrupted, but I still get the error message.

My question is: How can I revert to the previous version of Seahorse? I note that on the Seahorse web site only .tar packages are available and I don't really know how to install using .tar packages. Any help appreciated

---

### Post by Ziggy72 on 2006-09-03
The problem is solved! It seems that when Seahorse was updated, the new version updated its gnome icons and one of the gnome icons upon which another launcher depended was not replaced with an icon named Seahorse-key.png.Instead, the Gnome icon was changed to Seahorse.png and Seahorse-key.png was deleted. Changing the launcher icon to Seahorse.png solved the problem.

That said, I would still like to have guidance on how to deal with .tar files if a .deb version of a program is not available. Thanks.

---

