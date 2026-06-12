---
title: "No icons"
date: 2009-03-01
forum: Desktop Environments
---

### Post by steigerjb on 2009-03-01
I had been trying to get xwinwrap to work with no avail. I want to get rid of it so I can have my desktop back. (When xwinwrap is installed there are no more desktop icons) How do I remove xwinwrap??? HELP

I have tried the

killall xwinwrap
kill xwinwrap

nothing....

I have been told it may not be xwinwrap that hid my desktop. No desktop icons or right click on desktop

HELP HELP!!

---

### Post by JECHO on 2009-03-01
> **steigerjb said:**
> I had been trying to get xwinwrap to work with no avail. I want to get rid of it so I can have my desktop back. (When xwinwrap is installed there are no more desktop icons) How do I remove xwinwrap??? HELP

I have tried the

killall xwinwrap
kill xwinwrap

nothing....

I have been told it may not be xwinwrap that hid my desktop. No desktop icons or right click on desktop

HELP HELP!!



try this:

alt+f2 and type in:

```
gconf-editor
```

then browse to apps > nautilus > preferences

...scroll down to "show_desktop" and if the box isn't checked. check it and reboot. now you should be able to right click and have icons :)


hope that works.

---

### Post by steigerjb on 2009-03-02
found a solution:

alt+f2
"gconf-editor"
apps->nautilus->preferences.
click "show desktop"
alt+f2
"nautilus"

---

