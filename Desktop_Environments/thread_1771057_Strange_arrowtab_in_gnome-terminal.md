---
title: "Strange arrow/tab in gnome-terminal"
date: 2011-05-30
forum: Desktop Environments
---

### Post by Pixel on 2011-05-30
I have this strange little tab/triangle thing in the corner of all my gnome-terminals, I assume it's there for resizing purposes, but it looks really bad and was wondering if there's a way to remove them, I've attached a screenshot incase that helps.

Thanks.

---

### Post by stinkeye on 2011-05-30
Screenshot???

If it's the resize handles, add this to your **~/.gtkrc-2.0** file.
Create the the file if you don't have one.
```
style "default-style"
{
  GtkWindow::resize-grip-height = 0
  GtkWindow::resize-grip-width = 0
}

class "GtkWidget" style "default-style"
```

---

### Post by Zookalicious on 2011-12-13
Works great stinkeye, thanks.

---

