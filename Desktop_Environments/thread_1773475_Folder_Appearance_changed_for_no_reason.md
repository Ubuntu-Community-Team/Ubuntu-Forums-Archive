---
title: "Folder Appearance changed for no reason"
date: 2011-06-02
forum: Desktop Environments
---

### Post by X10A on 2011-06-02
I'm running Natty with the ambience theme. For some reason, my folder appearance has changed without me doing anything. [See its present state here.]("http://www.mediafire.com/i/?n00g8bfyr2qu0qc")

How do I get it back to the default setting?

---

### Post by Copper Bezel on 2011-06-02
Damn. I thought this had actually been fixed in 11.04. 

Your theming isn't being *changed* - it's completely crashing. Try 

```
killall gnome-settings-daemon

gnome-settings-daemon
```

If that works, we can set it up to a script in Startup Applications.

---

### Post by X10A on 2011-06-02
Booted up this morning, and lo and behind, folders are back to normal.  Weird...but thanks for your advice. Will try that if this happens again.

---

