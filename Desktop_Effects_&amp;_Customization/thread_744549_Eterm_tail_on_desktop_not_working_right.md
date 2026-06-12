---
title: "Eterm tail on desktop not working right"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by fuhreal on 2008-04-03
Hi All,

So i'm trying to get a tail of syslog working correctly on my desktop using Eterm.

There are 3 issues I can't figure out ...

1.  I want it to always stay on the desktop even when i use CTRL+ALT+D to show the desktop (gnome) and i can't figure out how to do this.

2. When i add the tail command to session start, it won't be transparent however if I launch the same command during my session, it shows up exactly how i want (minus the #3 issue)

3. I'd like it to not have a pannel/taskbar place holder

this is the command I am using ..
```

Eterm -x -O -g=120x10+0+1300 --no-cursor --scrollbar off -f lightgrey --buttonbar off -e tail -f /var/log/syslog &
```


Hope that makes sense.....  

Also, it seems to be lacking a little... is there a way to get more messages / information to show up?  Maybe console message?

Thanks in advance..

---

