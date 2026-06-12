---
title: "Java plugin"
date: 2007-03-12
forum: Desktop Environments
---

### Post by JoeS on 2007-03-12
I want to download a Java plugin for my web browser (firefox).  Where should I install it?
Is it better in the root directory or home?
If root where would it go?

---

### Post by taurus on 2007-03-12
Either

```
/usr/share/firefox/plugins
```
or
```
~/.mozilla/plugins
```

---

### Post by JoeS on 2007-03-13
Thanks for your response.

I installed the plugin in ~/.mozilla/pluggins.  It didn't work for the website.

The instructions for the Java Runtime Environment plugin says to enable and configure:

# Go to the plugins sub-directory under the Mozilla installation directory
cd <Mozilla installation directory>/plugins
# In the current directory, create a symbolic link to the JRE ns7/libjavaplugin_oji.so file Type:
ln -s <JRE installation directory>/plugin/i386/ns7/libjavaplugin_oji.so

This didn't work either.

Can you tell me what I need to do?

---

