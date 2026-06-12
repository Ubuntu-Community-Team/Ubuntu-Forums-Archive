---
title: "&quot;Current Theme&quot; missing in Tweak Tool"
date: 2014-01-25
forum: Desktop Environments
---

### Post by Deucalion29710 on 2014-01-25
I just fully wiped my hard drive and started fresh with a new install of Ubuntu GNOME 13.10.  While I was customizing everything I noticed that "Current Theme" or formerly known as Metacity option is completely missing in GNOME Tweak Tool.  How can I fix this or get the option back?  Thanks in advance.

---

### Post by ibjsb4 on 2014-01-26
I am not familiar with gnome-tweak-tool, but I wonder.  Metacity is itself a window manager and Unity uses compiz as a window manager.  Were you running something different before?

---

### Post by Frogs Hair on 2014-01-26
The window decortication / title-bar option does appear in the Tweak Tool in Ubuntu 13.10 + the Gnome Shell 3.8., I haven't used the Ubuntu Gnome release which would be using Mutter instead of Compiz. I can't verify if the selection you are looking for should be there or not.

---

### Post by qwazix on 2014-02-01
opening dconf-editor searching for metacity and changing the theme fixes this

---

### Post by Deucalion29710 on 2014-02-02
I ended up fixing it by purging tweak tool and installing an older verson.

---

