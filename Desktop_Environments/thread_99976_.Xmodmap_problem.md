---
title: ".Xmodmap problem"
date: 2005-12-06
forum: Desktop Environments
---

### Post by ivanii on 2005-12-06
I have followed tutor to add support to 7-wheel mouse, and created ~/.Xmodmap

It worked fine, but unfortunatly after Ubuntu once asked me whether to load .Xmodmap, I answered no and checked "don't ask me again".

Now, I can't restore my settings back. Probably there is a way to reset this, but I can't find it.

---

### Post by FLeiXiuS on 2005-12-06
Hahaha!  We share commonalities.  I did the same EXACT thing when X  notified me of the new configurations.  Easily managable.

Open a terminal and enter the following.
```

$ sudo gedit /etc/X11/gdm/PostLogin/Default

```
This file is used to tell GDM to run specific commands before LOGIN's.  This is crucial for Xmodmap.  So your going to tell GDM to execute ~/.Xmodmap upon LOGIN.
```

#!/bin/sh

. ~/.Xmodmap

```

That should do it...logout and log back in to see if alls well!

---

### Post by ivanii on 2005-12-06
Thanks.

---

