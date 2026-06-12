---
title: "Restoring Firefox Prompts for Profile"
date: 2010-06-23
forum: Desktop Environments
---

### Post by user2037 on 2010-06-23
When configured to save and restore running applications (System, Preferences, Start-up Applications, Options) the restoration of Firefox instances prompts for profile.

In my case Firefox was running with several different profiles. Each one was started with "-no-remote" and "-P [profile-name]".

Any ideas? Would it be possible to auto-close only Firefox windows?

---

### Post by lovinglinux on 2010-08-05
You could add a script to your startup to kill firefox.

```
killall firefox-bin
```

---

