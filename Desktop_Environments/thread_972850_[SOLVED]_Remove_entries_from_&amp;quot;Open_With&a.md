---
title: "[SOLVED] Remove entries from &amp;quot;Open With&amp;quot; list"
date: 2008-11-06
forum: Desktop Environments
---

### Post by n00g33 on 2008-11-06
Hi.

I've been playing around with opening files for a few days since I installed Intrepid. I seem to have collected a lot of unneeded entries in my "Open With" list - mostly custom commands I put in. (The list when you right-click and choose "Open with other application").

I was wondering if anyone knew how to remove these custom commands from the list.

Thanks in advance.

---

### Post by divot_powell on 2008-11-06
Hi,

If you right-click on the specific file and go to properties, in the "Open With" tab you can add/remove/select the default programs you would like to appear in the menu.

Cheers,

Dan

(This is using ubuntu 8.10, with gnome but may work for other versions)

---

### Post by n00g33 on 2008-11-06
Noooo.... it's not the MENU I'm talking about. It's the full list..

...the one where you right click on a file and select **Open with other Application...**. You should get a whole list. I've got random entries stuck in there. There is no add/remove button in this area.

I tried to explain it in the first post...

---

### Post by divot_powell on 2008-11-06
Ah, sorry, didn't realize. I've done some routing around and found this:[http://ubuntuforums.org/showthread.php?p=2161195#8]("http://ubuntuforums.org/showthread.php?p=2161195#8").

With all of the custom one's I've made they appeared as items in ```
~/.local/share/applications/
```
and from what small tests I've done removing the relevant items there removed them in my open with list.

There are two mime files in mine that I have left well alone, and if you don't recognize an item in the list my advice is to also leave it well alone, or make a copy of it somewhere else before removing it.

Hope that helps,

Cheers,

Dan

---

### Post by n00g33 on 2008-11-06
Thank Divott.. I was looking for that. I wish there was instructions on where to find all these things. Would make my life a lot easier.

---

