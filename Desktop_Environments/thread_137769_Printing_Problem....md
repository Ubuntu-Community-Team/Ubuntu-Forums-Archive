---
title: "Printing Problem..."
date: 2006-02-28
forum: Desktop Environments
---

### Post by xXx 0wn3d xXx on 2006-02-28
I am proformance crazy :) I tweak lots of things. I removed update notifier from starting with gnome but I also removed something like gnome-cups-icon. Now, after I removed it, I can't print. When I go under Admin>Printing I get Cups Server can't be contacted. I have it to run at startup. Now can someone tell me the thing I need under Preferences > Sessions > Current Session and can you tell me the name, order, and style. Please, I need this to work. It is something like gnome-cups-icon. :cry:

---

### Post by o_fortuna on 2006-02-28
[QUOTE=MasterChief1234]I am proformance crazy :) I tweak lots of things. I removed update notifier from starting with gnome but I also removed something like gnome-cups-icon. Now, after I removed it, I can't print. When I go under Admin>Printing I get Cups Server can't be contacted. I have it to run at startup. Now can someone tell me the thing I need under Preferences > Sessions > Current Session and can you tell me the name, order, and style. Please, I need this to work. It is something like gnome-cups-icon. :cry:[/QUOTE]
Mine says this:
```
gnome-cups-icon --sm-config-prefix /gnome-cups-icon-zX3W7G
```
The order is 50, the style is restart.

However, have you checked to be sure that Printer Service (cupsys) is enabled in System-->Preferences-->Services? Checking that box might be the best way to make sure you get exactly what you want.

---

### Post by xXx 0wn3d xXx on 2006-02-28
let me try that....

---

### Post by xXx 0wn3d xXx on 2006-02-28
do you have the style and order ?

---

