---
title: "&quot;man ln&quot; in Terminal"
date: 2009-03-22
forum: General Help
---

### Post by Shiv4m on 2009-03-22
Okay after for so long I might be able to make my Java work with a little bit more help...

I first need to install the FireFox plugin **"libjavaplugin_oji.so"** which I have no idea on how to do.

Then I need to go into symlink this:

```
lrwxrwxrwx  1 avenger users  57 May 28 2007 libjavaplugin_oji.so -> /usr/lib/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so
```

Thanks for the help...

---

### Post by apmcd47 on 2009-03-22
> **Shiv4m said:**
> Okay after for so long I might be able to make my Java work with a little bit more help...

I first need to install the FireFox plugin **"libjavaplugin_oji.so"** which I have no idea on how to do.

So where is this plugin at the moment? the following would copy it from the current directory to the plugin directory:
```
sudo cp libjavaplugin_oji.so /usr/lib/jre1.5.0_01/plugin/i386/ns7

```> 
Then I need to go into symlink this:

```
lrwxrwxrwx  1 avenger users  57 May 28 2007 libjavaplugin_oji.so -> /usr/lib/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so
```

Thanks for the help...
This will link it into the current directory:
```
ln -s /usr/lib/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
```
Does that help?

Andrew

---

### Post by Shiv4m on 2009-03-22
No, I don't have the plugin, I need it...

---

### Post by Shiv4m on 2009-03-23
Where can I download the plugin?

---

