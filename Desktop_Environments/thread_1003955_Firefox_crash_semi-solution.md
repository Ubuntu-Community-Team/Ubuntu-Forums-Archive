---
title: "Firefox crash semi-solution"
date: 2008-12-06
forum: Desktop Environments
---

### Post by superheavy on 2008-12-06
I installed Ibex and was struck by the wonderful user interface.  Unfortunately, the firefox not starting struck me even harder.
My error consisted of clicking the firefox icon , watching the loading bar appear at the bottom control panel, then watching the bottom bar disappear in a hurry.  
 I did a stack trace and found the following evidence amongst a bunch of other babble:

```

access("/home/dallas/.mozilla/firefox", F_OK) = -1 EACCES (Permission denied)
mkdir("/home/dallas/.mozilla/firefox", 0700) = -1 EACCES (Permission denied)
```

where dallas is my username.  The situation I used , which may not be approved by other linux users was to "carpet bomb" change permissions

```
sudo chown -R dallas:dallas .mozilla
```
```
sudo chmod -R go+rx .mozilla
```

firefox should start after this , hope this helps someone.

---

