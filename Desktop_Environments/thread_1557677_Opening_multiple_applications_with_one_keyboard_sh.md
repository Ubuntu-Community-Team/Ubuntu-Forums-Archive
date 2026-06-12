---
title: "Opening multiple applications with one keyboard shortcut"
date: 2010-08-21
forum: Desktop Environments
---

### Post by konrad_f on 2010-08-21
Hi,

I would like to open multiple applications with one keyboard shortcut but don't get it running. When I add (open "System" > "Preference" > "Keyboard Shortcuts"; clicked "Add" ) a new shortcut and enter many commands in the "Command" field e.g. "gnome-terminal & xeyes" only the first application is started. I also tried to set up a shell script that contains the application calls and then use "gnome-terminal -x "sh /path/to/the/script.sh" but then I get the error message "There was an error creating the child process for this terminal". Any suggestions how to get this working?

Cheers

---

### Post by sharathcshekhar on 2010-08-21
To use gedit and gvim as 2 applications, you can create a script like
```

#! /bin/bash
gvim &
gedit &

```
chmod +x script.sh

And then add this to the command in shortcuts: /full/path/script.sh
And you are done.

---

### Post by konrad_f on 2010-08-21
Not sure what I did differently but your suggested solution work fine. Thanks a lot!

---

### Post by Gaygerbil on 2010-08-23
In case you're curious the reason your shortcut wasn't working is cuz you only had one '&' symbol instead of two.

It should be something like this:

```
vlc && exaile && skype
```

That would launch all three. When you only put 1 '&' it'll just launch the first app and ignore the rest of your command cuz it doesn't recognize it.

---

