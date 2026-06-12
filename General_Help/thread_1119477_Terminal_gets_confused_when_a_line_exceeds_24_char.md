---
title: "Terminal gets confused when a line exceeds 24 characters"
date: 2009-04-08
forum: General Help
---

### Post by slk0 on 2009-04-08
If I type more than 24 characters into the terminal window, navigation keys like Home or Ctrl-Left cause the cursor to become out of sync with the display.

For example, if I type "aaaaaaaaaaaaaaaaaaaaaaaaa" and hit Home, the cursor jumps to somewhere in the middle instead of the beginning of the line, and other strange things occur as I continue to edit the line.

If the line is less than 25 characters long, all the navigation keys behave properly.

This is Ubuntu 8.10, running bash in the Gnome terminal.  Does anyone know what's going on?  Thanks in advance.

---

### Post by slk0 on 2009-04-10
Problem solved.

For the benefit of others: this happens if your $PS1 has ANSI escapes that are not properly surrounded by \[ and \].

---

