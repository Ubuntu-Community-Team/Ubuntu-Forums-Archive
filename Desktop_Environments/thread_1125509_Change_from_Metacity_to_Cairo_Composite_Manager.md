---
title: "Change from Metacity to Cairo Composite Manager"
date: 2009-04-14
forum: Desktop Environments
---

### Post by chrismja on 2009-04-14
I'm running Ubuntu 9.04. I have been using Compiz for desktop effects which I really like, but unfortunately it is causing some seriously problems with running Virtualbox. So I decided to try a different composite manager to see if it would work with Virtualbox. I installed from Cairo Composite Manager and uninstalled Compiz. But when I run cairo-compmgr from terminal- it says "Screen 0 already has a composite manager running, try to stop it before run cairo-compmgr" metacity is running and that's what is causing the error. But how do I stop metacity and/or replace it with cairo-compmgr?

---

### Post by kawaji on 2009-04-14
I think you need to disable metacity's built-in composite manager.
```
$ gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

---

### Post by chrismja on 2009-04-14
Thanks I'll try that. Just in case Cairo doesn't help with the Virtualbox issue, how would I go back and enable the composite manager in Metacity? I assume that I would just change the "false" to "true"?

---

### Post by kawaji on 2009-04-14
> I assume that I would just change the "false" to "true"?
Yes

---

