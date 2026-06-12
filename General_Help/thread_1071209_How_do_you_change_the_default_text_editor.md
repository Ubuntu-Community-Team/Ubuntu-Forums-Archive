---
title: "How do you change the default text editor?"
date: 2009-02-15
forum: General Help
---

### Post by JohnJSal on 2009-02-15
I've read about:

sudo update-alternatives –config editor

but this seems to offer only a handful of choices. What if I want to change my default editor to Scite, or some other downloaded program. Is this possible?

---

### Post by ch0d3 on 2009-02-16
[http://tips.webdesign10.com/how-to-change-the-default-text-editor-on-ubuntu-with-nautilus](http://tips.webdesign10.com/how-to-change-the-default-text-editor-on-ubuntu-with-nautilus)

[http://lmgtfy.com/?q=change+default+text+editor+ubuntu](http://lmgtfy.com/?q=change+default+text+editor+ubuntu) :P

---

### Post by JohnJSal on 2009-02-16
> **ch0d3 said:**
> [http://tips.webdesign10.com/how-to-change-the-default-text-editor-on-ubuntu-with-nautilus](http://tips.webdesign10.com/how-to-change-the-default-text-editor-on-ubuntu-with-nautilus)

[http://lmgtfy.com/?q=change+default+text+editor+ubuntu](http://lmgtfy.com/?q=change+default+text+editor+ubuntu) :P

Thanks. My own google search turned up the same results, most of which give the command I quoted in my original post. But the first link looks helpful, so I'll give that a try. Hopefully Nautilus isn't something additional to install though.

---

### Post by mc4man on 2009-02-16
The first link is your best way, just take it a step or 2 further if needed.
Install your new editor
right click on a text file -> properties -> open with.
If it's not in the list, go 'add'
If it's not in that list then go 'use a custom command'
Use as a command whatever will open your new editor from the terminal.
If your new editor installed to /usr/bin then usually it will just be it's name, for instance scite, just figure it out from the terminal if needed.

> Hopefully Nautilus isn't something additional to install though

If your using ubuntu then nautilus is already installed (it's your file manager

---

### Post by JohnJSal on 2009-02-16
> **mc4man said:**
> The first link is your best way, just take it a step or 2 further if needed.
Install your new editor
right click on a text file -> properties -> open with.
If it's not in the list, go 'add'
If it's not in that list then go 'use a custom command'
Use as a command whatever will open your new editor from the terminal.
If your new editor installed to /usr/bin then usually it will just be it's name, for instance scite, just figure it out from the terminal if needed.



If your using ubuntu then nautilus is already installed (it's your file manager

Thanks!

---

