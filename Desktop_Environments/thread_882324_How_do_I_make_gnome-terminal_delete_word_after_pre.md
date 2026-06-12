---
title: "How do I make gnome-terminal delete word after pressing ctrl+backspace?"
date: 2008-08-06
forum: Desktop Environments
---

### Post by gprefix on 2008-08-06
Apparently both Backspace and Ctrl+Backspace emit the same byte sequence (I tested by typing Ctrl-v first). How can I configure the terminal to distinguish between these so that I can bind Ctrl+backspace to backward-kill-word in inputrc file for readline? I am looking for a configuration file I can modify (like keytab file in konsole). Here is an excellent tutorial for konsole, but the entry for gnome-terminal is missing: [https://help.ubuntu.com/community/HowToReadline](https://help.ubuntu.com/community/HowToReadline)

Thanks

---

### Post by pauper on 2008-08-09
Ctrl-w does backward word rubout by default.

---

### Post by sayakb on 2008-08-09
Alt+Backspace erases the last word.

---

