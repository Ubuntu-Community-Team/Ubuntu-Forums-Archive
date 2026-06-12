---
title: "Vim / Gvim configuration question"
date: 2007-12-06
forum: Desktop Environments
---

### Post by Paulr-55 on 2007-12-06
I set lines=47 in my .vimrc which makes Gvim's window full height on my desktop whenever it starts up. However, when I invoke Vim at the terminal it goes haywire with this setting.

Is there a way to specify that setting for the GUI window only? I don't need Vim to change the geometry of my terminal window.

I am using Gutsy/Gnome. Thanks for any insights.  ;-)

---

### Post by jmc1024 on 2007-12-06
Googling, I found:
if has("gui_running")
  set columns=100
  set lines=37
endif 
but it doesn't seem to work here.
Mark

---

### Post by Paulr-55 on 2007-12-06
Mark, I just tried that and it seems to do the trick here.

Thanks, Paul

---

### Post by jmc1024 on 2007-12-07
Interesting...  If I run gvim from a terminal, then the window is not adjusted to lines and columns values.  But if I double click on a source file for the file manager, then it works.
Mark

---

### Post by hugmenot on 2007-12-08
The simple solution is to add all Gvim specific lines to the .gvimrc file, not to .vimrc.

---

