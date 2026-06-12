---
title: "Help : how to enable visual effect in my pc"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by mincho on 2007-10-29
i ve just installed ubuntu 7.10 gutsy on my pc .Intel GMA X3000 with i810 drivers ... 

 when i enable visual effects the error occur...Desktop effects could not be enable.. please solve my problem.

---

### Post by rundee_f on 2007-10-29
can u specify what error that occur??

---

### Post by Therion on 2007-10-29
> **rundee_f said:**
> can u specify what error that occur??
If I read the OP correctly, the specific error being generated is "Desktop Effects Could Not be Enabled".

**mincho:** Most likely you need to install xserver-xgl to get Compiz Fusion up and running.

```
sudo apt-get install xserver-xgl compizconfig-settings-manager
```
Log out and back in and run Compiz-Fusion (compiz &#8211;replace) and your desktop effects should work.

---

### Post by shibumathur on 2008-02-21
compiz aleardy install but when i want to open prefernces it doenst open 
and when i typed command "ccsm" it show the flowing error[SIZE="4"] "**AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'**"[/SIZE]

---

### Post by shibumathur on 2008-02-21
compiz aleardy install but when i want to open prefernces it doenst open
and when i typed command "ccsm" it show the flowing error "AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'" after that i uninstall ccsm would i do next can anybody help me...........

---

