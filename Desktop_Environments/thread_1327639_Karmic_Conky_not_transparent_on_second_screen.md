---
title: "Karmic: Conky not transparent on second screen"
date: 2009-11-15
forum: Desktop Environments
---

### Post by 10o on 2009-11-15
Since the installation of Karmic I am not able to get Conky to be displayed transparent on my second (right) screen anymore. On the left screen, the transparency settings work just fine, but that is not where I want Conky to be. I am using the same settings as in Jaunty.

Has anybody figured out how to get this fixed?

Applying the following changes to .conkyrc makes Conky transparent on the second screen, but it makes all desktop icons disappear...

```
own_window yes -> own_window no
own_window_type normal -> own_window_type override
own_window_transparent yes -> no changes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager -> removed
```

---

