---
title: "Make certain windows appear without titlebar etc?"
date: 2009-03-28
forum: General Help
---

### Post by detroit/zero on 2009-03-28
How can I make a window appear without any titlebar, buttons, etc?

I'm trying to use ImageMagick's display command to show various pictures, but they appear in separate windows, each with its own decorations. I'd rather just have the images appear without window decorations, if possible.

---

### Post by VCoolio on 2009-03-28
If you are running compiz you can set this in the window decoration plugin via system > preferences > compizconfig settings manager. In the entry field for decoration windows fill in !(class=imagemagickorsomethinglikethat). Click the + button to the right of the field and grab the imagemagick window to check its class.

---

### Post by detroit/zero on 2009-03-28
Thanks for the reply.. I actually just found (via Google) a page at the CF forums that said to do exactly that.

Works like a charm. Thanks again!

---

