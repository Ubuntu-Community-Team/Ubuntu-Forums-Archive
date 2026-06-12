---
title: "Problem installing libgtk2.0-dev, a weird dependency error"
date: 2006-09-02
forum: Desktop Environments
---

### Post by leeyee on 2006-09-02
Hi guys,
I'm not sure if you guys also encountered any problems with this issue. I'm using Ubuntu Dapper which was upgraded from Breeze with "apt-get dist-upgrade" several monthes ago. And of course I did a "apt-get update" before I post here.

I want to install libgtk2.0-dev so that I can write some GTK+ programme on Dapper. However, after marking libgtk2.0-dev to be installed in Synaptic I was told some dependency packages such as libglib2.0-dev, etc. Then the problem came, it told me this:
```

libgtk2.0-dev:
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libcairo2-dev but it is not going to be installed

```
After this, I referred to libcairo2-dev, and want it marked to be installed. Then I got this:endless loop
```

libcairo2-dev:
  Depends: libcairo2 (=1.0.4-0ubuntu1) but 1.2.0-0ubuntu1quinn2 is to be installed

```

That's really odd. It seems that I've just been in an endless loop. I also did the same thing under shell using
```

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install libcairo2-dev

```
but only got:
```

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.2.0-0ubuntu1quinn2 is to be installed
E: Broken packages

```


:mad: Now, I have no idea about that anymore, anyone can give me some advices? Thanks alot!

---

### Post by leeyee on 2006-09-02
well, I've corrected this. 
I just forced the libcairo2 version to 1.0.4-0ubuntu1, and reinstalled it. After this everything worked.

---

