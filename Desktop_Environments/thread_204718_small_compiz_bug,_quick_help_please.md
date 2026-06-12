---
title: "small compiz bug, quick help please"
date: 2006-06-27
forum: Desktop Environments
---

### Post by truenemesis on 2006-06-27
So I went through this tutorial. [http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+howto](http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+howto)

And when I ran "thefuture", I got this message.

```

gnome-window-decorator, Failed to load shadow imag es
compiz.real: No composite extension

```

I tried this
```

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

```

And i still got the message. Can anyone quickly help me? Thanks.

---

### Post by chadwick359 on 2006-06-27
What hardware/drivers are you using? Also, while Phg maakes an awesome HowTo, HIs actually installs and uses the Dapper Repo compiz packages, which are much slower and less feature complete. I would suggest instead reading the beginning of my HowTo and get the latest and greatest compiz packages (warning, may be broken today) and then continue with the gdm.conf configuration as Phg explains it.

---

