---
title: "Incompatibility between xterm and gnome-terminal"
date: 2007-05-05
forum: Desktop Environments
---

### Post by longlivedeath on 2007-05-05
I want to map Ctrl-Backspace to backward-kill-word in zsh, but can't get it to work with gnome-terminal. With xterm, one can use "bindkey '^H' backward-kill-word", but in gnome-terminal both Backspace and Ctrl-Backspace get mapped to '^?', so this method doesn't work. Is there some way to make gnome-terminal distinguish between Backspace and Ctrl-Backspace like xterm does? Unfortunately, i can't switch to xterm since I also use tilda.

---

### Post by longlivedeath on 2007-05-05
Bump.

---

### Post by longlivedeath on 2007-05-07
Bump.

---

### Post by metalheart on 2007-05-07
In gnome-terminal navigate to Edit -> Profiles. Select Default and click Edit. Select Compatibility. Maybe settings for the Backspace key are what you need?

---

### Post by longlivedeath on 2007-05-07
Thank you for your answer, but this was actually the first thing I tried, and unfortunately it didn't work. Guess I have to file a bugreport.

---

### Post by longlivedeath on 2007-05-07
[http://bugzilla.gnome.org/show_bug.cgi?id=436697](http://bugzilla.gnome.org/show_bug.cgi?id=436697)

---

