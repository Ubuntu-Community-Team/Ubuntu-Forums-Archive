---
title: "Installing .deb packages with root access issues"
date: 2005-12-29
forum: General Help
---

### Post by rowck001 on 2005-12-29
I installed alacarte menu editor from a .deb package.

dpkg would not let me install unless using root priviliges:

I used su --> and input my root password

then dpkg -i alacarte_0.8-0ubuntu1_all.deb

The software installed but will only work when using a sudo prefix and changes will not reflect in my user login.

How do I make it work with my user account?

---

### Post by darth_vector on 2005-12-29
you should be able to run as a user by going to the gnome menu -> accesories.


EDIT: dpkg can only ever be run as root.

---

### Post by az on 2005-12-29
[QUOTE=rowck001]
The software installed but will only work when using a sudo prefix and changes will not reflect in my user login.

How do I make it work with my user account?[/QUOTE]

Whether you installed it in a root shell or with sudo, this is a packaging problem, ad not your fault.  The person who made the package did not make it properly.

Maybe you can change the permissions of the executable yourself?

---

