---
title: "how to add shortcut in the tray"
date: 2007-02-12
forum: Desktop Environments
---

### Post by jeisma on 2007-02-12
hi!

i'm using xubuntu 6.10.

i want to add a couple of shortcuts (launcher) in the system tray.

i used to do that with ubuntu by simply right-clicking a shortcut, then (i think) add to launcher.

any ideas how?


thanks!

joey

---

### Post by paparucino on 2007-02-13
> **jeisma said:**
> 

i want to add a couple of shortcuts (launcher) in the system tray.

i used to do that with ubuntu by simply right-clicking a shortcut, then (i think) add to launcher.

any ideas how?


I use two methods.
The first is to create, via terminal, a sym-link 
```

ln -s /your appl path/your appl  /home/Desktop/your appl

```
then drag the icon on the desktop to the tray ad modify accordingly, the remove thee icon on the desk top.

Second method is to add an appl, via alacarte, in Accessories then "Add to launcher".


Hope it help

---

### Post by philws on 2008-04-23
Sometimes your applications need specific variables set in the environment before they can be successfully launched (e.g. IntelliJ IDEA 7.x requires the JDK_HOME environment variable set). In which case an easy way to handle this is to use a "command" in the launcher properties of the form:

/bin/sh -c "export JDK_HOME=*/some/path* && /*path/to/idea/installation*/bin/idea.sh"

I'm using the normal shell here with a "command string" that exports the required environment variable and then executes the required application, idea.sh. You can chain as many steps as necessary using ";" or "&&" as separators ("&&" is handy since following commands are only executed if the earlier command(s) succeed).

---

