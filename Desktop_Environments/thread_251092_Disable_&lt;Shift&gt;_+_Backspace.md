---
title: "Disable &lt;Shift&gt; + Backspace"
date: 2006-09-04
forum: Desktop Environments
---

### Post by RuarriS on 2006-09-04
How can I disable the annoying Shift + Backspace keyboard combo that restarts X, without disabling all my other keyboard combinations for xgl + compiz?

---

### Post by spvo on 2006-09-05
To disable the shift backspace thing you need to have this command run at startup.

xmodmap -e "keycode  22 = BackSpace"

I just put it into its own script and added that script to the startup programs.  You probably disabled all the other hot keys if you tried that xmodmap fix that forces the us keymap.

---

