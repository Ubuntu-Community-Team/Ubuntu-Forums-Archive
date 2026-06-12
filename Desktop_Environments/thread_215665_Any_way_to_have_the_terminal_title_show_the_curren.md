---
title: "Any way to have the terminal title show the currently running program?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by monkeypunch on 2006-07-14
Is there any way to set the dynamic title for gnome-terminal to include the name of the currently running program, like the OS X terminal can do?

It would be useful for example to easily distinguish between the window that contains irssi and the others in the window list.

Does anyone know of a way to do this? I'd consider other temrinal programs as well, but would prefer to stick with the GNOME terminal if possible.

---

### Post by Zenham on 2007-09-14
Documentation here:

[http://www.ibiblio.org/pub/Linux/docs/HOWTO/Xterm-Title]("http://www.ibiblio.org/pub/Linux/docs/HOWTO/Xterm-Title")

---

### Post by Nythain on 2007-09-14
it depends on the terminal emulator you are using... at a quick glance it looks like you can name the title in gnome-terminal by calling it with the -t TITLE option, where TITLE is what you want it to say in the title bar, so if you were using it to run top you could do something like
gnome-terminal -e top -t Top
should do the trick, you get the point... its a little different in the other terminal emulators

---

### Post by Zenham on 2007-09-14
I believe he means dynamically change, not setting the title upon opening a terminal.

For that, he needs the above documentation. A mirrored version also exists at [http://www.linux.org/docs/ldp/howto/Xterm-Title.html]("http://www.linux.org/docs/ldp/howto/Xterm-Title.html")

---

