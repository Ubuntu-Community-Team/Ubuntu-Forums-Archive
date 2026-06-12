---
title: "Problem getting apps to start with OpenBox"
date: 2009-05-17
forum: General Help
---

### Post by thegreenblob on 2009-05-17
Hey everyone.

I'm trying to get openbox to start 3 apps at start up.

pypanel, xcompmgr & cairo-dock.

I am using autostart.sh and I have pypanel working using this:

```
pypanel & 
if pgrep pypanel 
then exec openbox 
else pypanel && exec openbox 
fi
```

Which I found the solution for on a thread somewhere on here ):P

But, I tried the same thing with xcompmgr & cairo-dock, but they still did not start up automatically. I run them manually with gmrun and they work fine but they refuse to start up automatically.

So anyone have any ideas?

---

### Post by thegreenblob on 2009-05-17
Nevermind I solved it with:

```
pypanel & xcompmgr & cairo-dock -o &
if pgrep pypanel
then exec openbox 
else pypanel && exec openbox 
fi
```

Not sure why it would matter if they were on their own line or not but w/e. It works so I'm happy. :)

---

