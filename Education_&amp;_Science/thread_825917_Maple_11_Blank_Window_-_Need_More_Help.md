---
title: "Maple 11 Blank Window - Need More Help"
date: 2008-06-11
forum: Education &amp; Science
---

### Post by karasuman on 2008-06-11
I searched for help with this problem, and I found this thread: [http://ubuntuforums.org/showthread.php?t=450064&highlight=maple+blank](http://ubuntuforums.org/showthread.php?t=450064&highlight=maple+blank)

Unfortunately, following those instructions doesn't help me, and it's probably because there's an implied obvious step that I'm missing.

When I type "export AWT_TOOLKIT=MToolkit && xmaple" into the terminal, I get this response:

bash: xmaple: command not found

I have Maple 11 installed.  The link to the launcher is /home/beth/maple11/bin/xmaple.  Just like the old thread, I can load the program by turning off my pretty desktop effects, but I get a blank window if I don't do that first.

---

### Post by mervin on 2008-06-12
Try entering the full path to xmaple i.e.

"export AWT_TOOLKIT=MToolkit && /home/beth/maple11/bin/xmaple"

---

### Post by karasuman on 2008-06-12
That did it.  Thank you!  Will I have to launch Maple like this every time?  (If so, is there a way to just fix it once and for all?  Someone in the other thread mentioned editing a bash file or something, but I don't even know what that means.)

---

