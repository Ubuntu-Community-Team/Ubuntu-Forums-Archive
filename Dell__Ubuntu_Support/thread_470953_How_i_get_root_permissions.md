---
title: "How i get root permissions"
date: 2007-06-11
forum: Dell  Ubuntu Support
---

### Post by wreddoug on 2007-06-11
I whant to install java in my ubuntu but when i whant to do anything in de usr it keep telling me y have no root permissions

What can i do

---

### Post by nvteighen on 2007-06-11
Very simple: you must use the "sudo" command before the command that needs root permissions.

Example:
```

sudo shutdown -h now

```

Cheers!

---

### Post by xthund3rh3adx on 2007-06-11
if installling in terminal:

use 

sudo COMMAND-HERE

then type the password you used during setup of ubuntu (probably your users password)

or, to get a full root terminal, create a pasword for root:
sudo passwd root

then type a password you would like

then enter:
su

and type the password you just made.

---

