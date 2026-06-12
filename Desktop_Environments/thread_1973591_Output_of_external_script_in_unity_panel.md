---
title: "Output of external script in unity panel"
date: 2012-05-05
forum: Desktop Environments
---

### Post by bshowup on 2012-05-05
Hi,

Did some customization of my top panel in Ubuntu 12.04 with Unity and python appindicator, by combining several examples to a little python script that lets you display the output (stdout) of an external script (e.g. "free") or something like that, in your Panel.

Thought i could share this.

[Screenshot]("http://www.showup.at/unity-panel-text.png")

Python Code:

```

#!/usr/bin/env python

import sys

if (len(sys.argv) < 3):
    print '\nDisplays the output of an external script in your Panel\n\nUsage: script.py /path/to/external/script interval(seconds)\n';
    sys.exit(0)
    
import gtk
import appindicator
import subprocess as sub
import string as s
 
FREQUENCY = int(sys.argv[2])

class UtextPanel:
    def __init__(self):
        self.ind = appindicator.Indicator("UTextPanel","",appindicator.CATEGORY_APPLICATION_STATUS)
        self.ind.set_status(appindicator.STATUS_ACTIVE)
        
        self.menu_setup()
        self.ind.set_menu(self.menu)

    def menu_setup(self):
        self.menu = gtk.Menu()

        self.quit_item = gtk.MenuItem("Quit")
        self.quit_item.connect("activate", self.close)
        self.quit_item.show()
        self.menu.append(self.quit_item)

    def main(self):
        self.update()
        gtk.timeout_add(FREQUENCY * 1000, self.update)
        gtk.main()

    def close(self, widget):
        sys.exit(0)

    def update(self):
        p = sub.Popen(sys.argv[1],stdout=sub.PIPE,stderr=sub.PIPE)
        output, errors = p.communicate()
        self.ind.set_label(s.strip(output))
        return True


if __name__ == "__main__":
    indicator = UtextPanel()
    indicator.main()


```

---

### Post by beruic on 2012-05-31
Works beautifully for my project specific status hacks :)
Only thing I find odd is that it tries to display more than one line at a time. Would be cool if it would just flush what's there when a new line is entered, and print the new stuff. That way you could use sleeps to rotate between info.

---

### Post by bshowup on 2012-06-05
Thanks for your input.

Just showing changed data surely would be more efficient.
I solved the "multiple lines" issue with filtering out new lines in my external scripts.

Since i'm running this now for a few weeks, and it seems to get native to my ubuntu desktop, i'm planning to implement thinks like you mentioned :)

---

### Post by beruic on 2012-06-05
Please notify here if you create a project page or a ppa or something :)

Also, perhaps it would be nice if it was possible to have multiline output shown when you click.

---

