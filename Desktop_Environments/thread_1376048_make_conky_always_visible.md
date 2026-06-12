---
title: "make conky always visible"
date: 2010-01-08
forum: Desktop Environments
---

### Post by 3948ctyj on 2010-01-08
how do I make conky visible on my browsing screen..??? its on my desktop ok and I tried the "always on visible workspace thing....
and can I get voltage on conky???  Toshiba laptop..

---

### Post by marco123 on 2010-01-08
[http://ubuntuforums.org/showthread.php?t=281865&highlight=show+.conkyrc](http://ubuntuforums.org/showthread.php?t=281865&highlight=show+.conkyrc)

That thread has absolutely tons of useful conky info, might be helpful.

---

### Post by stinkeye on 2010-01-08
If you mean above other windows
Change these settings in your conky
```
own_window_type [COLOR="#ff0000"]normal[/COLOR]
own_window_hints undecorated,[COLOR="Red"]above[/COLOR],skip_taskbar,skip_pager
```

---

### Post by 3948ctyj on 2010-01-08
I just saved a new theme code and it works but now the desktop icons disappear until you hover over them..
I deleted the start up code...  I would like it to start up    but need correct command...
and this icon thing sucks...

---

### Post by stinkeye on 2010-01-08
> **3948ctyj said:**
> I just saved a new theme code and it works but now the desktop icons disappear until you hover over them..
I deleted the start up code...  I would like it to start up    but need correct command...
and this icon thing sucks...
Post your conky config.

The default config that came with conky is found in /etc/conky/conky.conf
If you have no ~/.conkyrc , running the command conky will load /etc/conky/conky.conf

You can run any conky conf with the command *conky -c /path/to your/conky*
[_**[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]**_]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

