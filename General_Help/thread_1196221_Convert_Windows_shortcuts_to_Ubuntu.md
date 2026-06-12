---
title: "Convert Windows shortcuts to Ubuntu?"
date: 2009-06-24
forum: General Help
---

### Post by I-Imaging on 2009-06-24
Is there any way to convert they standard shortcut keys from windows to Ubuntu. Like win+e = explorer window or cntrl+shift+esc = taskmanager. I've found out how to do some manually but not all of the ones that I typically use. 

It would be nice if there was a way to convert them so I don't forget anything. 

Thanks.

---

### Post by mbeach on 2009-06-24
I don't know of one that creates all of XP's shortcut keys, but you can edit keyboard shortcuts under System -> Preferences -> Keyboard shortcuts.

You can add custom ones there as well. Click the 'Add' button, Type a name like "Run Web Browser", then put the command for your browser. Once its in the list, click on the 'disabled' in the Shortcut column and use your keyboard to set the shortcut. This is a bad example as I believe there is one there already under Desktop called Launch web browser.

Were there any in particular from Windows that you are looking for equivalents?

---

### Post by I-Imaging on 2009-06-25
Oops... I totally missed the keyboard shortcuts application. I feel pretty dumb right now. :$

When I try to edit the keyboard shortcuts I press the windows key + e for explore but it only registers the windows as "super L" and won't use the + e. 

I assume I'm doing something wrong but what?

---

### Post by mbeach on 2009-06-25
No, you are doing nothing wrong - I get the exact same behaviour. I believe this is a requested feature, but some discussion on who is going to 'fix' it.

[http://brainstorm.ubuntu.com/idea/2051/](http://brainstorm.ubuntu.com/idea/2051/)

In that link's discussion, there is mention that you can manually set it but I have not tried.
> 
Currently you can only set Super by itself from the System -> Preferences -> Keyboard Shortcuts dialog. It is possible to set, but you have to start gconf-editor from the command line. In gconf-editor -> / -> apps -> metacity -> window_keybindings you have to manually type the combination, instead of pressing the desired key combination.


---

