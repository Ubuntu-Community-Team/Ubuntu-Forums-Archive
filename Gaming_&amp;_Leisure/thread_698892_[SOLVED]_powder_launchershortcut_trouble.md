---
title: "[SOLVED] powder launcher/shortcut trouble"
date: 2008-02-16
forum: Gaming &amp; Leisure
---

### Post by eilu on 2008-02-16
Powder keeps saving in /home; when I contacted the developer about changing the save directory, he said:
> POWDER saves its files in the directory it is started from.  In the case of your shortcut, _if you edit the short cut properties there likely is an option there to say where to start the program_.  That is likely set to home.  _Change that to your desired directory and you are good to go_.
Is there a way to do that in gnome? (i.e., tell the app to start from a specified location) Can't find it in Alacarte...

---

### Post by eilu on 2008-02-17
...found a workaround; I mucked around and made a shell script to launch it, seems to do the trick. The script, should anyone be interested, is:
```
#!/bin/bash
cd /usr/games/powder100/
exec /usr/games/powder100/powder
# end, save in ~/bin/ , chmod +x , have your desktop shortcut launch
# this script instead of the application itself.
```

---

### Post by hyperair on 2008-02-17
Are you sure that's right? Perhaps you should make the second line something like: "cd ~/.powder". Then it'll automatically save all its settings in its own settings folder in your home directory.

---

