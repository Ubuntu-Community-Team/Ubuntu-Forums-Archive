---
title: "XFCE and xmodmap at startup"
date: 2015-12-01
forum: Desktop Environments
---

### Post by Jacqes on 2015-12-01
Hello,

I'm new to ubuntu and was trying to remap some keys.

I apologize for posting this because it has been answered before but none of the solutions could help in my case.

I already modified the .Xmodmap file. Using the command:

```
xmodmap .Xmodmap
```

verified that the remap works.

The problem comes when I want to make the changes permanent.

Already tried using:

[LIST]
[*]gnome-session-properties 
[*]creating a .xinitrc (also using sleep 10 && xmodmap .Xmodmap) 
[*]linking it to .xsession 
[/LIST]

Could someone help me here?

Thanks in advance.

EDIT: 

Finally It worked adding to startup applications an order to run the command "xmodmap .Xmodmap"

I had done this before without working so I don't know what happened.

Hope this helps someone.

---

