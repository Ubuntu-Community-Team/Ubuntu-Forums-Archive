---
title: "Moving buttons back to the left?"
date: 2011-12-11
forum: Desktop Environments
---

### Post by R3cKL3SS_aM on 2011-12-11
I ran this command line:
```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close

``` to move my buttons to the right and now want to move them back to the left. Is there a command line to do so?

---

### Post by BC59 on 2011-12-11
A graphical tool to make all these changes is Ubuntu Tweak. From a terminal:

```
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update
sudo apt-get install ubuntu-tweak-0
```

---

### Post by BC59 on 2011-12-11
If you need the terminal commnands

Right Side
```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "menu:minimize,maximize,close"
```

Left Side
```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
```

---

