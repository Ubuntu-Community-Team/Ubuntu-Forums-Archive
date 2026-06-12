---
title: "pygtk error with ccsm"
date: 2007-11-25
forum: Desktop Effects &amp; Customization
---

### Post by Kralizec on 2007-11-25
I've searched far and wide and haven't been able to find a suitable answer. When I try to run the CompizConfig Settings Manager, it returns this error: 

```

alterdeshasses@TyphoonStruggle:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
PyGtk 2.10.0 or later required

```

According to synaptic and apt I have the most up-to-date python-gtk2, so I have no idea how to go about fixing this problem. It literally just popped up, although it may have something to do with the myriad problems I had trying to get AWN curves working (which I never did, kept returning a [FONT="Courier New"]make[/FONT] error).

So any help someone can give me would be much appreciated, it would be lovely to be able to change my Compiz settings.

---

### Post by Forlong on 2007-11-25
What's the output of ```
dpkg -l | grep python-gtk2
```

---

### Post by Kralizec on 2007-11-25
```

alterdeshasses@TyphoonStruggle:~$ dpkg -l | grep python-gtk2
ii  python-gtk2                                2.12.0-0ubuntu2                         Python bindings for the GTK+ widget set
ii  python-gtk2-dev                            2.12.0-0ubuntu2                         GTK+ bindings: devel files

```

Thanks for the help.

---

### Post by Forlong on 2007-11-25
It appears that you are right. Unfortunately, I don't know what you did to make those AWN-curves work, so I have no idea what could be the problem right now.
Obviously ccsm can't recognize that pygtk is installed, maybe reinstalling it could work:
```
sudo apt-get install --reinstall python-gtk2
```

---

### Post by Kralizec on 2007-11-25
*Sigh* Still no luck. Any other ideas, please let me know.

---

