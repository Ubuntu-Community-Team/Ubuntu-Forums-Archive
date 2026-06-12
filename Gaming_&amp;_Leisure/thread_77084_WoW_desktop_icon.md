---
title: "WoW desktop icon"
date: 2005-10-16
forum: Gaming &amp; Leisure
---

### Post by inz on 2005-10-16
I have WoW running in an acceptable manner, but I can't seem to get it to launch from the desktop, that is, it does launch, but I cannot type in any scandinavian characters then. If I open a terminal window and type in lang=no_NO and then cedega WoW.exe, it will work perfectly.

When I run it without the lang parameter I get this:
Warning: Language 'en_SE' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US

Any hints on how I can get it to run straight from the gnome desktop with the right characters? It'd be more convenient that way. :)

---

### Post by Perfect Storm on 2005-10-16
That can be fixed with a little script.

Okay, first create a text document called RunWow.sh
Open it and write:

```

#!/bin/bash

lang=no_NO
<insert the command that makes Wow running>

```

next:
```

chmod +x RunWow.sh

```

Now instead making a shortcut to the current wow, you make a shortcut to this script.


.:=The AI Dude=:.

---

### Post by inz on 2005-10-16
Tried that actually, didn't work. :/
I can start RunWow.sh from a terminal window and it will work, if I start RunWow.sh from the desktop, it doesn't.

---

### Post by Perfect Storm on 2005-10-16
Okay. Try this:

The shortcut to the script needs to be marked as 'Run in Terminal'.
(It's next to the icon: [no icon] when making the launcher).

---

### Post by seethru on 2005-10-16
or in your shortcut try sh /path/to/RunWoW.sh

---

### Post by inz on 2005-10-17
This is really weird, but still nothing.
I can start an xterm and run it, but making a new launcher with the run in terminal option gives me an extra terminal window, but no scandinavian letters... using sh in front of the path didn't work either.

*very much confused*

---

### Post by MaX on 2005-10-17
en_SE is that a real language???
sv_SE is my guess.

---

### Post by elldiablo on 2006-06-15
hey  can you help me out please i have  a problem can you fix me your  runwow becasue mien is damadge or corrupt  THnx in advance

if you wont you can send me a email  with the link  of uploaded file like rapidshare or something like that

---

### Post by corys on 2006-07-01
were can i get runwow? **HELP**

---

### Post by lotheac on 2006-07-03
Don't 'Run in terminal', do "export lang=no_NO" instead of just "lang=no_NO". At least this is what works for me with TinyFugue (with the exception that I export LC_ALL).

Alternatively I suppose you could just put it all on one line, ie. "lang=no_NO <command to start wow>".

---

