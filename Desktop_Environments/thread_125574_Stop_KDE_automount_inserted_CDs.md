---
title: "Stop KDE automount inserted CDs"
date: 2006-02-04
forum: Desktop Environments
---

### Post by agenkin on 2006-02-04
How can I tell kde to *not* automount CDs and DVDs when I insert them into the drives?  Currently, when I insert any optical media, KDE launches Konquerror to show its contents: I want to stop that from happening.  I have device icons disabled (I have *all* icons disabled in the Desktop preferences for that matter).

This is driving me nuts: I looked all over the KDE preferences and didn't find a  toggle for this. Any help would be greately appreciated.

---

### Post by T*&amp;1p87)v# on 2006-02-04
Hi,

I just did that on my KDE 3.5

start kcontrol
and go to Peripherals ==> Storage Media

from there I went throught the list of all the available media, selected the
 "Do Nothing" action and then pressed the "Toggle as Auto Action" button. 
After that when I plugged my iPod in it did not automount it, also no window
pop up
:)
hope that helped.

---

### Post by christianbrahms on 2006-02-04
If you don't have KDE 3.5, you can do it on the system level... The package responsible for that is ivman

sudo gvim /etc/ivman/IvmConfigActions.xml

The syntax is pretty obvious, with syntax highlighting for xml files (GVim does this) you'll have no problem reading that file. Just comment the things out you don't need.
You don't even have to restart afaik.

Yours
cb

---

### Post by T*&amp;1p87)v# on 2006-02-04
Thanks cb,

did not know that, added it to my notes :)

---

