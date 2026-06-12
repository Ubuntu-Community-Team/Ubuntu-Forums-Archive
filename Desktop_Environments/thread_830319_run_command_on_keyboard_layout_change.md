---
title: "run command on keyboard layout change"
date: 2008-06-15
forum: Desktop Environments
---

### Post by starenka on 2008-06-15
Hi, i want to change spell checker languages on keyboard layout change.

I figured out how to change the checker from commandline...

```
kwriteconfig --file kdeglobals --group KSpell --key KSpell_Dictionary czech
```

..and i was planning to use it with the command issued on a layout change (see pic)

[IMG]http://crap.starenka.net/kbd.png[/IMG]

unfortunately the command is not editable thru kcontrol UI. I grepped config files for such params and it seems to be actually generated from kxkbrc file.

So the question is... is there a way how to issue a command on keyboard layout change? Or is there any other way how to change spell checker "dictionary" on kb layout change?

thx st.

---

