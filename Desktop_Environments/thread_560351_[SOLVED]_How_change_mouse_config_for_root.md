---
title: "[SOLVED] How change mouse config for root?"
date: 2007-09-26
forum: Desktop Environments
---

### Post by undecidable on 2007-09-26
I have set up my mouse to doubleclick rather than singleclick to open a folder/file.

However on those occasions when I need to do something as root 
(eg copy a file)
and run "kdesu konqueror"
(or open the folder as root from the context menu)
the mouse is set up as single click
which for me is a bit dangerous.

I can't work out how to change it to double click for root.
I can for example run "mouse" as a user
but if I try to run "kdesu mouse"
it asks for my password
then gives me "command 'mouse' not found'.

Nor can I find any config files to edit.

Any insight into this curious little brick wall appreciated.

---

### Post by jim_p on 2007-09-26
Just a suggestion...
I dont know how are things are set in kde but you can open konqueror as root, go to konquerors preferences and alter the root preferences from there
One other thing would be to run the "mouse preferences" as root. eg (in gnome)

gksu gnome-mouse-properties

---

### Post by undecidable on 2007-09-26
Thanks

1.  mouse properties aren't set from Konq, so 1st idea is not possible.

2.  There is no kde-mouse-properties.  I can run "mouse" (with alt-F2) but not "kdesu mouse", so I suspect "mouse" might be a user based symlink but can't determine the target.  A filesearch for "mouse" yielded nothing.

---

### Post by jim_p on 2007-09-27
I installed kde-core to search for the mouse equivalent in kde.

It seems that the command that applies to the mouse properties is 
```
kcmshell mouse
       or
kdesu kcmshell mouse
``` to run it as a root.
I confirm that both work but i dont know if altering the root settings will apply the settings systemwide.
Please post back if it worked



Excuse me for the delay but I am really tired lately :(

---

### Post by undecidable on 2007-09-27
Many thankyous!
Yes it worked.  

I had not heard of kcmshell, but now know its purpose. 
Also now know I can get a full list of configuration  modules with:
  kcmshell --list.

I have now also been able to determine where the mouse settings are stored,
so if necessary they can be edited by hand:
.  cursor themes are in kcminputrc.
.  but the important stuff, eg single/double click is in kdeglobals.  
There is obviously one in ~/.kde/share/config and in root/.kde/share/config,
with the default in /usr/share/kubuntu-default-settings/...

mc

---

