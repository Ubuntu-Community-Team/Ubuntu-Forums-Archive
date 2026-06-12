---
title: "Help updating packages"
date: 2009-04-22
forum: General Help
---

### Post by Tanthal on 2009-04-22
Ive been trying to update my packages and update manager crashes.  It gives me this error message


An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--2009-04-21' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list, E:The list of sources could not be read.'

  I'm not sure what I did but im sure it wasnt good if anyone could help would be greatly appreciated

---

### Post by zvacet on 2009-04-22
In terminal type 

```
cat /etc/apt/sources.list.d/winehq.list
```

and post it here.

---

