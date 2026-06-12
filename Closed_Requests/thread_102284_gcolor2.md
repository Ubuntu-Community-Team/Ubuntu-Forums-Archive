---
title: "gcolor2"
date: 2005-12-11
forum: Closed Requests
---

### Post by malte on 2005-12-11
A simple color chooser. It's in dapper already, that should be trivial backporting :)

---

### Post by benplaut on 2005-12-11
ditto... it looks useful

---

### Post by sjoeboo on 2005-12-12
jsut built the backport fine, will notify list.

---

### Post by jdong on 2005-12-12
Approved and sent off.

---

### Post by ardchoille on 2005-12-12
In the meantime, you can do this:

1. create a new file, copy the below code into it and give it a filename of color-picker.py or something.

```

#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk

class ColorPicker:
    def close(self, attributes):
        gtk.main_quit()

    def __init__(self):
        self.window = gtk.ColorSelectionDialog('Select Color')
        self.window.ok_button.connect("clicked", self.close)
        self.window.cancel_button.connect("clicked", self.close)
        self.window.show()

    def main(self):
        gtk.main()

prog = ColorPicker()
prog.main()


```

2. run the file in a term (or create a new menu item for it) with:

```
python color-picker.py
```

It's a simple python app and I know it isn't the same as gcolor2, but it will suffice until gcolor2 is available with sudo apt-get install.

---

### Post by benplaut on 2005-12-13
[QUOTE=ardchoille]In the meantime, you can do this:

1. create a new file, copy the below code into it and give it a filename of color-picker.py or something.

```

#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk

class ColorPicker:
    def close(self, attributes):
        gtk.main_quit()

    def __init__(self):
        self.window = gtk.ColorSelectionDialog('Select Color')
        self.window.ok_button.connect("clicked", self.close)
        self.window.cancel_button.connect("clicked", self.close)
        self.window.show()

    def main(self):
        gtk.main()

prog = ColorPicker()
prog.main()


```

2. run the file in a term (or create a new menu item for it) with:

```
python color-picker.py
```

It's a simple python app and I know it isn't the same as gcolor2, but it will suffice until gcolor2 is available with sudo apt-get install.[/QUOTE]

very nice... no longer will i have to use the gnome-panel background color selection :p

---

