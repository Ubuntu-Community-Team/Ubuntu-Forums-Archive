---
title: "emerald theme help"
date: 2009-02-13
forum: General Help
---

### Post by squelchy451 on 2009-02-13
Hi.

I had a Ubuntu 7.10 and recently upgraded to 8.04.

When I click on a theme in the Emerald theme manager with the Compiz Fusion running, the theme does not change.

How do I fix this?

Thanks:confused:

---

### Post by overdrank on 2009-02-13
Hi and try the command with the alt, F2 keys  ```
emerald --replace
```TO activate the theme

---

### Post by squelchy451 on 2009-02-14
oh wow 

it worked!

Thanks a lot. :KS

What exactly did I do there?

---

### Post by mcduck on 2009-02-14
You started Emerald. ;)

---

### Post by dj722000 on 2009-02-14
I don't know about other versions, but under 8.10 you can got to SYSTEM -> Preferences -> Sessions and give the command emerald --replace in there to start when it boots. That's how I do it. Then you don't have to mess with it on restarts, it just automatically starts.

---

### Post by squelchy451 on 2009-02-14
it stopped working...

So did magic lamp! i did some hacking to make the max # of waves = 0 and now its not working at all

T.T HALP!!!

---

### Post by phantom3113 on 2009-02-14
Try installing "fusion icon" if you don't have it already. This puts a tray icon up on the bar (if you have one at the top of the screen) and makes it much easier to switch between window decorators (metacity/emerald) and visual effect managers (gtk/compiz). You'll probably have to add fusion icon to the sessions so it starts up upon login, but it might fix your issues.

---

