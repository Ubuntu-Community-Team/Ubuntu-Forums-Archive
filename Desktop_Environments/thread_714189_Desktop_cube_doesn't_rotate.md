---
title: "Desktop cube doesn't rotate"
date: 2008-03-03
forum: Desktop Environments
---

### Post by PolecatIV on 2008-03-03
Hi You all! I know, maybe this is a repost, but i just can't get the cube working. I got a problem with the alt + ctrl + button1 in "initiate", in the rotate cube setup. Every time i set the configuration (es. <Control><Alt>Button1), the General tab close itself, I open it and the command is back to "none" (see the screenshot included). The cube works, but only with the key arrows left and right, but there's no way with the mouse. 
Some suggestion? Thanks

---

### Post by fracturedmorals on 2008-03-03
have you tried middle-clicking on the desktop itself without any keys?

---

### Post by Het Irv on 2008-03-03
I think Clicking and holding both the left and right mouse buttons will turn on free rotate.

---

### Post by PolecatIV on 2008-03-03
Thanks for the answers dudes, tried both, but no results, just the selection rectangle :confused: I don't understand why, the setup disapper...

---

### Post by Het Irv on 2008-03-03
There is a seperate plug-in for rotating the cube (Why, I have no idea).  Check to make sure that it is enabled.

---

### Post by PolecatIV on 2008-03-03
Yep.. is already on. Well... no Yatzee tonight! :lolflag:

---

### Post by benerivo on 2008-03-03
How about right clicking on the action name (ie. the word initiate' in your pic), and selecting 'reset to defaults'. Or maybe change the configuration file directly. Try adding this to your /home/ben/.config/compiz/compizconfig/Default.ini file

```
[rotate]
as_initiate = ,<Control><Alt>Button1,,0,false
```

---

### Post by PolecatIV on 2008-03-03
Thanks, but i havent Default.ini in that directory, i got only "config" contains this:

[gnome_session]
profile = 
plugin_list_autosort = true

I tried paste the rows you said, but i don't think i put that in the right file :(

---

### Post by erginemr on 2008-03-03
And trivial maybe, but also make sure that you have 4 virtual desktops enabled.

---

### Post by PolecatIV on 2008-03-03
Yes, it is. But some good news, with the "accelerator key" the cube now rotates, but still not with the button1,2 or 3

---

### Post by benerivo on 2008-03-03
PolecatIV, my files (ie. the Default.ini that i mentioned) may be different to yours as i am using Debian unstable and not Ubuntu, so the way the compiz packages work may be different. However, your compiz settings will still be stored somewhere inside your home directory, and probably in a humanly readable format. If you can find out where you may be able to fix it.

Maybe your problem stems from something else that already uses the Ctrl Alt Button1 combination on your desktop?

---

### Post by PolecatIV on 2008-03-03
No.. :/ i tried gconf-editor, but it tells me i can't edit the row "initiate_button", "key not writable... this thing is drive me crazy, thanks for support dudes!

---

