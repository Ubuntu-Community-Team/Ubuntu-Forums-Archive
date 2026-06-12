---
title: "Menu editor broken"
date: 2006-06-01
forum: Desktop Environments
---

### Post by shame on 2006-06-01
After launching the Alacarte menu editor a couple of times it failed to show so I tried running alacarte in a terminal and got this - ```
Theme
    __addTheme(subtheme)
  File "/usr/lib/python2.3/site-packages/xdg/IconTheme.py", line 298, in __addTheme
    __parseTheme(os.path.join(dir,theme, "index.theme"))
  File "/usr/lib/python2.3/site-packages/xdg/IconTheme.py", line 309, in __parseTheme
    theme.parse(file)
  File "/usr/lib/python2.3/site-packages/xdg/IconTheme.py", line 23, in parse
    IniFile.parse(self, file, ["Icon Theme", "KDE Icon Theme"])
  File "/usr/lib/python2.3/site-packages/xdg/IniFile.py", line 26, in parse
    if not os.path.isfile(filename):
  File "/usr/lib/python2.3/posixpath.py", line 203, in isfile
    return stat.S_ISREG(st.st_mode)
RuntimeError: maximum recursion depth exceeded
```

There are actually hundreds of those  File "/usr/lib/python2.3 lines but they are all olong the same lines.

---

