---
title: "Error found when loading /etc/profile"
date: 2019-11-15
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2019-11-15
I get this error in one user every time I log in :

```
etc/profile.d/input-method-config.sh: line 10:
/etc/X11/Xsession.d/70im-config_launch: No such file or directory
As a result the session will not be configured correctly.
You should fix the problem as soon as feasible.
```

What is the error?

There is no directory:
[HTML]/etc/X11/Xsession.d[/HTML]

How do you "fix the problem"?

---

### Post by rsteinmetz70112 on 2019-11-15
Running im-config  get:
```
# im-config
Gtk-Message: 22:31:11.394: GtkDialog mapped without a transient parent. This is discouraged.
```

Followed by a pop up :

```
Current configuration for the input method:
 * Active configuration: missing (normally missing)
 * Normal automatic choice: ibus (normally ibus or fcitx or uim)
 * Override rule: zh_CN,fcitx:zh_TW,fcitx:zh_HK,fcitx:zh_SG,fcitx:ja_JP,fcitx:ko_KR,fcitx:vi_VN,fcitx
 * Current override choice:  (en_US)
 * Current automatic choice: ibus
 * Number of valid choices: 2 (normally 1)
The override rule is defined in /etc/default/im-config.
The configuration set by im-config is activated by re-starting X.
Explicit selection is not required to enable the automatic configuration if the active one is default/auto/cjkv/missing.
  Available input methods: ibus xim
Unless you really need them all, please make sure to install only one input method tool.
```

---

### Post by rsteinmetz70112 on 2019-11-18
OK 

I removed and reinstalled the im-config package where where ```
 70im-config_launch
``` is supposed to be, with no luck. The file was still missing.

I found a backup? directory```
 /etc/X11- 
```and copied```
 70im-config_launch
``` into```
 /etc/X11/Xsession.d/
``` and the error message went away.

Not sure why reinstalling ```
im-config
``` didn't fix the issue. I'm wondering what else should be in  ```
/etc/X11/Xsession.d/
``` the only thing in it now is  ```
70im-config_launch
```

---

