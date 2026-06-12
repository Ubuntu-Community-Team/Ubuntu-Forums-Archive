---
title: "Unbind ctrl+/ from &quot;select all&quot; in 14.04"
date: 2014-10-01
forum: Desktop Environments
---

### Post by Thimoteus on 2014-10-01
I was trying to bind ctrl+/ to comment a line inside a gedit plugin and inadvertently discovered ctrl+/ seems to do the same thing as ctrl+a, but in any text area (gedit, firefox, leafpad, anything). I didn't find anything in my ~/.config/openbox/lubuntu-rc.xml which is the only place I've found to edit keyboard shortcuts. Does anyone know how to unbind this so I can use it in gedit?

---

### Post by vasa1 on 2014-10-01
> **Thimoteus said:**
> I was trying to bind ctrl+/ to comment a line inside a gedit plugin and inadvertently discovered ctrl+/ seems to do the same thing as ctrl+a, but in any text area (gedit, firefox, leafpad, anything). I didn't find anything in my ~/.config/openbox/lubuntu-rc.xml which is the only place I've found to edit keyboard shortcuts. Does anyone know how to unbind this so I can use it in gedit?
I agree that lubuntu-rc.xml doesn't have any way to handle how text is selected and that sort of makes sense because lubuntu-rc.xml is related to window manager functions alone and not to individual programs. It's up to the user to use "safe" keyboard shortcuts in rc.xml; otherwise, in case of conflict, I suspect the individual active (in focus) program's setting will prevail.

And ctrl+/ doesn't work, AFAICT, as you describe in LibreOffice Writer or in Geany which is why I suspect that the ctrl+/ ability to select all text in a text area is determined by each program's code and isn't "system-wide".

So maybe you need to hunt for what determines keyboard shortcuts **internal** to gedit.

---

### Post by Thimoteus on 2014-10-02
Well if it is program-specific then it's specific to firefox, leafpad, gedit, scratch-text-editor and chromium. In atom I can use the shortcut to toggle a comment but I'm not sure why I can set this shortcut in atom and not gedit.

---

### Post by vasa1 on 2014-10-02
> **Thimoteus said:**
> Well if it is program-specific ...
Isn't it?

If it isn't program-specific, it should be system-wide or ???

Ctrl+/ does nothing in JuffEd.
Ctrl+/ does nothing in Evince.

---

### Post by vasa1 on 2014-10-02
I've come across quite a few links on editing gedit shortcuts but it appears that the solution is version-dependent. Newer versions of gedit (and GNOME) may not be as customizable and solutions offered in older links may not apply to newer versions of gedit.

I don't know how recent [https://help.gnome.org/users/gedit/stable/index.html.en](https://help.gnome.org/users/gedit/stable/index.html.en) but it has a link to gedit shortcuts: ctrl+/ isn't listed, AFAICT. There's also a link to plugins which may provide additional customization. 

[http://superuser.com/questions/174267/can-you-do-keyboard-shortcuts-in-gedit](http://superuser.com/questions/174267/can-you-do-keyboard-shortcuts-in-gedit)
[https://answers.launchpad.net/ubuntu/+source/gedit/+question/98344](https://answers.launchpad.net/ubuntu/+source/gedit/+question/98344)
[http://superuser.com/a/476681](http://superuser.com/a/476681)
[http://askubuntu.com/questions/223986/custom-keyboard-shortcuts-in-gedit](http://askubuntu.com/questions/223986/custom-keyboard-shortcuts-in-gedit)

---

### Post by Thimoteus on 2014-10-13
If it isn't a default keybind then I must have done something at some point that made most of my programs interpret ctrl+/ as select all.

---

