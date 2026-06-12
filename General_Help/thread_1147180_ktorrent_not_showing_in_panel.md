---
title: "ktorrent not showing in panel"
date: 2009-05-03
forum: General Help
---

### Post by dandav101 on 2009-05-03
Hello, everyone. I have a problem with ktorrent. When I start it through the menu, it doesn't show up in the panel for selection, but when I go to the system monitor, it shows up there as sleeping. I can't seem to get it going. Does anyone else have this problem?

Dan

---

### Post by happyhamster on 2009-05-03
- Hello. Try launching ktorrent from a terminal. Go to Applications --> Accessories --> Terminal. Then type:

killall ktorrent

- to make sure ktorrent isn't running in the background. Then start ktorrent:

ktorrent

- and see if you get any error messages. If so, could you show them here?

Good luck.

---

### Post by dandav101 on 2009-05-03
Here is what it comes up with when I try it:

dan@OutsideTheBox:~$ killall ktorrent
dan@OutsideTheBox:~$ DCOP Cleaning up dead connections.
ICE default IO error handler doing an exit(), pid = 6762, errno = 11

---

### Post by happyhamster on 2009-05-03
- And what output do you get when starting ktorrent? Or is there no output?

ktorrent

- It would help if you also showed the output after killing ktorrent again:

killall ktorrent

- and then also the output of:

ps aux

(It will show which process the message "ICE default IO error handler doing an exit(), pid = " is talking about.) Thanks.

[edit: Which version of ubuntu are you running BTW?]

---

