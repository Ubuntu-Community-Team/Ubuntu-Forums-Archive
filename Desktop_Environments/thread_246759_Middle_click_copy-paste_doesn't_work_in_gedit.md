---
title: "Middle click copy-paste doesn't work in gedit"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Arevos on 2006-08-29
Highlighting a selection of text and middle-clicking in gedit does not copy the text, as is the Unix convention. Indeed, it doesn't seem to do anything at all. Is this a bug, or is there some option to turn this feature on? It seems rather strange that this should be missing from the standard Ubuntu text editor, or is it just me that has this problem?

Incidentally, it doesn't work with OpenOffice either, but then that's somewhat understandable, as it's a cross-platform application (that said, Firefox handle middle-clicks fine). Does anyone know of an option in OpenOffice that can enable this functionality?

---

### Post by lagagnon on 2006-08-29
They both work for me!

---

### Post by chingadero on 2006-11-02
I had the same problem in gnome-terminal and changed the Option "Emulate3Buttons" setting in /etc/X11/xorg.conf from "true" to "false"
under
Section "Input Device"
   Identifier  "Configured Mouse"
   ...

from
  Option      "Emulate3Buttons" "true"
to
  Option      "Emulate3Buttons" "false"

then I restarted the machine.

---

### Post by ninotob on 2007-01-13
Middle-click past ("MCP") does not work for me either, even after setting the 3button emulation to false.  Let me clarify, if I highlight something in another app, e.g., Firefox, I can MCP that text into gedit.  If I highlight something in gedit, and try to MCP it elsewhere inside that document, nothing happens.  Nor can I MCP text I copied from a document opened in gedit to other applications -- it's as if gedit does not put the selected text into the MCP buffer at all.  Indeed, if I first highlight something in Firefox, then highlight something in gedit, when I MCP into the terminal, it is the Firefox stuff that gets dumped.  So plainly, it is gedit which is failing to copy into the MCP buffer.

My question is this:  is there some obscure setting to get gedit to force it to conform to tradition, or is this some hare-brained idea that the tradition is wrong and should be verboten, even to those who like the convenience of having two paste buffers?

---

