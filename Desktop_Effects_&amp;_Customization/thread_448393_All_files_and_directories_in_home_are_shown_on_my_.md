---
title: "All files and directories in home are shown on my desktop"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by jueljust on 2007-05-19
[SIZE="4"]All files and directories in [FONT="Courier New"]~/[/FONT] is shown on my desktop, not the files and directories in [FONT="Courier New"]~/Desktop[/FONT]

how could i change this set?[/SIZE]

yours regards

---

### Post by Kimmik on 2007-05-19
Open the gconf editor(run **gconf-editor**) and go to /apps/nautilus/preferences/ and uncheck "desktop_is_home_dir".

Heres a screenshot 
[IMG]http://img227.imageshack.us/img227/9238/bildschirmfotokonfiguraki9.png[/IMG].

---

### Post by jueljust on 2007-05-20
[size=4]Great! It works!
Thank you very much![/size]

---

