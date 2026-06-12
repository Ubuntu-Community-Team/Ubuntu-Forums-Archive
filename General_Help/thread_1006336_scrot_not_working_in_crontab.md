---
title: "scrot not working in crontab"
date: 2008-12-09
forum: General Help
---

### Post by jmvidalvia on 2008-12-09
I made a simple script:
[HTML]
#!/bin/bash
scrot -d 4 'foto.png'
[/HTML]
When I execute the script from a terminal, it works ok.
But when I add it to the crontab of my user, then no "picture" is taken.
A clue may be that when I try to execute the script from a ssh connection, I get this message:
```
giblib error: Can't open X display. It *is* running, yeah?

```
I am afraid the user loging with the crontab has no way to access the X, although it is the same user.
Any ideas?
Thanks a lot!

---

### Post by false_chicken on 2011-01-28
I am also having this problem. I want a screenshot taken every so often. So I can see my own trends on my desktop lol. But scrot wont execute in cron. I get the same error from ssh.

---

### Post by false_chicken on 2011-01-28
[FONT=monospace]Wow I just noticed how old this thread is lol anyway for other people looking like me export the display:

[/FONT]"DISPLAY=:0 scrot -q 100 /home/user/screen.png"

---

