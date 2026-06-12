---
title: "etc\modules"
date: 2009-04-06
forum: General Help
---

### Post by wrose51106 on 2009-04-06
I need to edit / save this file but cannot. I have tried opening it normally and also from a terminal---> sudo pico modules. No go. I can edit but not save. Thanks in advance.

-Bill

P.S. Please remember to have your dogs spade or neutered.

---

### Post by drs305 on 2009-04-06
If pico is a graphical text editor, try:
```

*Graphical*:
gksudo pico /etc/modules
*Non-graphical:*
sudo pico /etc/modules

```
Make sure you include the path as in the above examples.

Use "gksudo" for graphical apps, "sudo" for terminal commands. In this case it was the path that was incorrect. "sudo" will work but can produce unexpected results. See:
[_http://www.psychocats.net/ubuntu/graphicalsudo_]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Iowan on 2009-04-06
If I try **sudo pico /etc/modules**, what I actually do is open the file with **nano**.  How did you attempt to save the file? Just to experiment, I edited my /etc/modules file, added an extra "comment" line, saved with CTRL-O, and exited with CTRL-X.

---

### Post by wrose51106 on 2009-04-07
Thanks for the replies, I was navigating to the directory and opening there from the terminal with Pico. I ended up running sudo pico /etc/modules and was able to save. Thanks guys!

-Bill

---

