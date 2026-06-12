---
title: "Alt-tab on multiple workspaces"
date: 2009-10-06
forum: Desktop Environments
---

### Post by Ryan_Singer on 2009-10-06
Hi Everyone,

I'm running Karmic, and I make frequent use of 4 workspaces to keep my windows from getting cluttered. The only thing that I find non-ideal is my decade-long trained reflex to use alt-tab to switch between windows and applications. Is there a way to configure GNOME so that alt-tab works across multiple workspaces?

--
Ryan

---

### Post by kanikilu on 2009-10-06
I've wondered this myself and browsed through gconf-editor, to no avail. The closest thing I've found is a package called SuperSwitcher:

[http://code.google.com/p/superswitcher/](http://code.google.com/p/superswitcher/)

I'm not at my Ubuntu machine now, though, so haven't tried it yet.

---

### Post by OpenGuard on 2009-10-06
Compiz can do that - [http://news.opensuse.org/wp-content/uploads/2007/08/shift-switcher.png](http://news.opensuse.org/wp-content/uploads/2007/08/shift-switcher.png) ( details inside the screenshot ).

---

### Post by COKEDUDE on 2011-01-31
Could you add the instructions? The picture is gone.

---

### Post by Forlong on 2011-02-01
[Ctrl]+[Alt]+[Tab] should be configured to do that by default in Compiz.

To change it to plain [Alt]+[Tab], run ```
ccsm
``` and go to the **Application Switcher** plugin and change **Next window (All windows)** to be initiated via **<Alt>Tab**

---

### Post by COKEDUDE on 2011-02-01
> **Forlong said:**
> [Ctrl]+[Alt]+[Tab] should be configured to do that by default in Compiz.

To change it to plain [Alt]+[Tab], run ```
ccsm
``` and go to the **Application Switcher** plugin and change **Next window (All windows)** to be initiated via **<Alt>Tab**

That doesn't work if the program is on a different workspace.

---

### Post by COKEDUDE on 2011-02-01
> **Forlong said:**
> [Ctrl]+[Alt]+[Tab] should be configured to do that by default in Compiz.

To change it to plain [Alt]+[Tab], run ```
ccsm
``` and go to the **Application Switcher** plugin and change **Next window (All windows)** to be initiated via **<Alt>Tab**

> **COKEDUDE said:**
> That doesn't work if the program is on a different workspace.

I found it :). Thx for pointing me into the general area. 

```
ccsm
```

**Static Application Switcher**, **Next window (All windows)**, to be initiated via **<Control><Alt>Tab**.

---

