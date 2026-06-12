---
title: "Terminal Server Client hangs"
date: 2009-04-03
forum: General Help
---

### Post by hikmatic on 2009-04-03
Terminal Server Client hang sometimes. Just thought to post this as no one has posted a fix to it  before. What you can do is 

Try pressing ALT+F2 then run "gnome-terminal".

once you get to the terminal run "ps -e"  Locate the "tsclient" process and kill it using the "kill" command. that should free up your mouse so you can work with rdp

---

