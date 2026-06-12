---
title: "Compiz - Cannot Check Effects"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by vejdi_86 on 2007-11-19
Hi
[[IMG]http://img140.imageshack.us/img140/8489/compizconfigkg0.th.jpg[/IMG]](http://img140.imageshack.us/my.php?image=compizconfigkg0.jpg)
look at this ...
I can`t check nothing.I think that i don`t have permissions.

How can I access to these effects.

10x

---

### Post by Forlong on 2007-11-19
What happens if you switch to the Flat-file Backend in Preferences?

---

### Post by vejdi_86 on 2007-11-19
Nothing.Just all effects don`t work. :)
When I add plugins in Preferences / Plugins  ... effects works.

---

### Post by Forlong on 2007-11-19
To correct permissions, you can use those commands:
```
sudo chown $USER:$USER $HOME -R
```
```
chmod -R u+rwX $HOME
```

---

### Post by vejdi_86 on 2007-11-19
10x i`ll try.

---

### Post by stldirty on 2007-11-19
ok, i had this exact same problem.  i somehow fixed it and i believe that the actual problem was that i didn't have "compiz-fusion-plugins-extra", "compiz-fusion-plugins-main", or "compiz-plugins" installed via synaptics.  tell me if this fixes the problem.

---

### Post by vejdi_86 on 2007-11-19
These packages are installed.I try to reinstall them but still not working well.

---

