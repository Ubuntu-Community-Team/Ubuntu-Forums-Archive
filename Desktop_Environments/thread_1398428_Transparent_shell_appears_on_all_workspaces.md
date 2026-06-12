---
title: "Transparent shell appears on all workspaces ?"
date: 2010-02-04
forum: Desktop Environments
---

### Post by uncle-c on 2010-02-04
Hello,
I found a relatively straightforward tutorial in the forums here on how to make a completely transparent shell with Compiz Fusion :

[http://ubuntuforums.org/showthread.php?t=859858](http://ubuntuforums.org/showthread.php?t=859858)

I followed it to the book and all seems fine except for one thing. Whenever I start the "transparent gnome-terminal" using either 

```
 ubuntu8-10:~$ gnome-terminal --window-with-profile=trans  
```

or FILE-->> OPEN TERMINAL-->>TRANS in a standard gnome-terminal , I get the transparent terminal opening not only on the current workspace but on all of the remaining other three as well ! I'm pretty certain this is a Compiz related matter as none of my other gnome-terminal profiles ( all of which are regular non-transparent) behave in such a way. Any idea on how I can solve this problem ?

Thanks
C

---

### Post by uncle-c on 2010-02-04
Problem solved. Just sharing the solution if it helps anyone in future.

From the tutorial :

[COLOR="Red"]"Go to the Window Rules plugin. Add "title=trans" to the following fields (This will turn the terminals into a widget-like windows):

    * Skip taskbar, Skip pager, Below, Sticky, Non resizable windows, Non minimizable windows, Non maximizable windows, Non closable windows."
[/COLOR]

Adding "title=trans" to the "Skip pager" field results in the transparent terminal being opened on all workspaces. Leave this field blank and the terminal will only open on your current workspace.

c

---

### Post by bonfire89 on 2010-03-24
thanks! :)

The tutorial I followed had actually covered that that and I filled in the fields, but, I forgot to check the check box to make them all applicable. ha!

anyways, this was the last step in getting everything to work, thanks!

---

