---
title: "How do I run programs on KDE start?"
date: 2005-12-31
forum: General Help
---

### Post by JamesNorris on 2005-12-31
I have a few programs that I want to run when I boot into Kde. I keep the last session open but some programs won't open again unless I remembered to keep a window maximised in the desktop. How do I make it so they run when I log into KDE?

---

### Post by audax321 on 2005-12-31
I haven't used KDE in a while, but I think you have to put a script in the /home/<username>/.kde/Autostart folder (make sure the script is executable).

e.g.

```

#!/bin/sh

# Script to start programs on KDE login:

# e.g. program entry:
if [ "$(pidof kcalc)" = "" ]; then
   kcalc
fi

```

You can also just list the executable files instead of the if statement, but the if statement will check to see if a previous instance is running and only start it if there isn't... that way if you kept your application maximized in the previous session, it shouldn't launch a second instance .... i think (assuming the script is run after KDE restores the old session) ;)

---

### Post by Freddy on 2005-12-31
All you have to do is put a symlink of the .bin file that you want to start when booting kde into /home/user/.autostart.   /// Freddan

---

### Post by JamesNorris on 2005-12-31
Thanks. That's just what I was after. 

:)

---

### Post by Naneau on 2005-12-31
you can also just drag icons for programs from your KDE menu into that folder, it's easier than creating shell scripts or symlinks :)

---

### Post by Freddy on 2006-01-01
> you can also just drag icons for programs from your KDE menu into that folder, it's easier than creating shell scripts or symlinks
Even smarter :).   /// Freddan

---

### Post by naught101 on 2008-05-12
thanks audax321... just what I needed. Pity there's no automated process for this (though kcontrol or something)

---

