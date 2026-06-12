---
title: "Compiz feature annoying"
date: 2006-08-26
forum: Desktop Environments
---

### Post by chrilleh on 2006-08-26
I'm running XGL+Compiz on a amd64.

If I am inactive for some time, like reading a pdf or something, then when i move the mouse again, the current windows "floats" back like the Exposé function. How do i turn this off? I don't want it to automatically do that?

---

### Post by deldredge on 2006-08-26
Is it because you're putting the mouse in the corners of the page? It does that automatically if you put the pointer in the corner. Other than that I don't know.

---

### Post by chicken101 on 2006-08-26
If it has something to do with the corner function, copy this into the terminal.

> gconf-editor

Goto programs, compiz, plugins, screen 0, options, and remove anything that says stuff about corners.

That will disable that function.;)

---

### Post by h00s on 2006-08-26
I don't think he thought about hot corner, but trailfocus plugin.
From help.ubuntu.com
[I]'Trailfocus

The 'trailfocus' plugin ads a 'visual trail' to window focus (It changes brightness, saturation and opacity of your windows depending on how long you have not used them).'[/I]

You can try adjust plugin options or remove it from active_plugins (ali in gconf-editor).

---

