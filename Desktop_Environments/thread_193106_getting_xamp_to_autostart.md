---
title: "getting xamp to autostart"
date: 2006-06-09
forum: Desktop Environments
---

### Post by puk on 2006-06-09
hi,

I wonder what I have to do to have xamp start automaticly on  sessionstart.

i've tried several different approaches but wasn't successful yet - is it because xamp has to be started with root-rights ?

Just to mention it starts flawlessly using ```
sudo /opt/lampp/lampp start
``` but as I said I would like it to start by itself.

help appreciated

---

### Post by puk on 2006-06-09
Ok,

it turns out that with ubuntu you have to start xamp in _every_ runlevel to make it autostart:

```
sudo ln -s /opt/lampp/lampp /etc/init.d/lampp
sudo update-rc.d lampp defaults
```

... if anybody knows a more elegant way - let me know.

---

