---
title: "Compositing problems with Docky, no window headers?"
date: 2010-09-04
forum: Desktop Environments
---

### Post by binarylife on 2010-09-04
When I logged in, none of my windows had tops (i.e. Window Title, Buttons for minimize, maximize, and close). 

Also docky give an error msg : Docky requries Composting to work probably. And I should click on compiz fusion icon and select compiz window manager every time I boot up. 

So how can I fix it please??

---

### Post by stinkeye on 2010-09-04
Two settings to check.

# gconf-editor /desktop/gnome/session/required_components/windowmanager **compiz**



# ccsm > Effects > window decoration > command```
gtk-window-decorator --replace
```

---

### Post by binarylife on 2010-09-05
> **stinkeye said:**
> Two settings to check.

# gconf-editor /desktop/gnome/session/required_components/windowmanager **compiz**

# ccsm > Effects > window decoration > command```
gtk-window-decorator --replace
```


When I checked the first command , windowsmanager value is metacity.
how can I change it ?

For the second command It gives me : gtk-window-decorator --replace
It is the same i thinks.

Thanks dude: )

---

### Post by stinkeye on 2010-09-05
> **binarylife said:**
> When I checked the first command , windowsmanager value is metacity.
how can I change it ?

For the second command It gives me : gtk-window-decorator --replace
It is the same i thinks.

Thanks dude: )

Just double click in the value field for window manager and type in
```
compiz
```
Compiz should load at start.

---

### Post by binarylife on 2010-09-05
> **stinkeye said:**
> Just double click in the value field for window manager and type in
```
compiz
```
Compiz should load at start.

Thanks It works now , but It took so long to open everything including Google gadgets and panels and docky ? (Is it because I've upgraded Ubuntu 10.04 to 10.10 beta)??Thanks Anyway

---

### Post by stinkeye on 2010-09-05
> **binarylife said:**
> Thanks It works now , but It took so long to open everything including Google gadgets and panels and docky ? (Is it because I've upgraded Ubuntu 10.04 to 10.10 beta)??Thanks Anyway
Don't really know.


But if your starting  fusion-icon in startup applications use 
```
fusion-icon -n
``` as the startup command.
The -n tells it not to load a window manager as compiz is loaded anyway.
May help, may not.

---

### Post by binarylife on 2010-09-05
> **stinkeye said:**
> Don't really know.


But if your starting  fusion-icon in startup applications use 
```
fusion-icon -n
``` as the startup command.
The -n tells it not to load a window manager as compiz is loaded anyway.
May help, may not.

Okay Thanks ,I appreciate your help.

---

