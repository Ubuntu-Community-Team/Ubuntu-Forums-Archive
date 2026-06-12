---
title: "gnome desktop launcher for bash script"
date: 2010-05-20
forum: Desktop Environments
---

### Post by toypest on 2010-05-20
How to create gnome desktop launcher for bash script?

1. i click the right button and select create laucher
2. i fill up name field and select my bash script in a command field.
3. click ok

the gnome desktop launcher is created, but when i click on it, nothing happens!

WHAT AM I DOING WRONG?

thank you.

---

### Post by kerry_s on 2010-05-20
is your script executable?

---

### Post by toypest on 2010-05-20
yes! i used chmod a+x *.sh on my bash script
and even tried chmod a+x ~/Desktop/mylauncher.desktop

---

### Post by angry_johnnie on 2010-05-20
> **toypest said:**
> yes! i used chmod a+x *.sh on my bash script


what you need to do is

```
chmod a+x /path/to/your/script
```

> **toypest said:**
> and even tried chmod a+x ~/Desktop/mylauncher.desktop

that's only if you wrote a .desktop file, which is not a script, really.

usually, a bash script would be something like this:

```
#!/bin/bash

some command
some other command

exit 0
```

you can name this file anything you want.  it doesn't necessarily need a *.sh* extension (or any other extension, for that matter).  if you're going to chmod it, make sure you chmod the correct file name.

you tried *.sh
and you also tried filename.desktop

so, what is it?  is it a .sh or a .desktop?
does it actually have an extension, or is it just a filename.
if it is just a filename, you need to chmod the filename only, without extensions.

another thing to consider is that if the file is not within your home directory, you'll need to **sudo** chmod a+x the file in question.

---

