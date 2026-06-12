---
title: "The F10-Shortcut-Problem ..."
date: 2011-12-22
forum: Desktop Environments
---

### Post by phil9r on 2011-12-22
Hiho guys,

sorry for disturbing you with this highly discussed topic but ... im getting crazy!

I installed the latest ubuntu yesterday and im configuring it step by step ...
as i love the midnightcommander you surely know that one needs the f10-key.

but as it comes to disable this shortcut, i think im too stupid dealing with it.
i unticked the boxes at edit->keyboard shortcuts (both of them), i deleted all values in the system while searching for F10 with the gconf-editor, i even found the bug-report at [the mailing lists](https://lists.ubuntu.com/archives/desktop-bugs/2007-February/077602.html).
using apt-get update and apt-get upgrade doesnt help anything at all - although it says "fix released". i cant get rid of this problem and im definetely going crazy solving this problem. 

thanks honestly for your help.
phil

---

### Post by gordintoronto on 2011-12-22
What computer? What keyboard? Did F10 work previously?

On my laptop, I have to hold down a Fn key to get any of the function keys to work as such, otherwise they do things like changing the volume. If you use MC, I doubt if that is your problem....

---

### Post by phil9r on 2011-12-23
IBM X40. Thougth it would fit into "desktop" issues ...
Its a subnotebook, not a netbook. 4 Years old. As it is a new installation, it didnt work previously - but it did with an old ubuntu-version.
Crashed my harddrive, so i had to buy a new one.
Other F-Keys work as they should i think. F1 opens help etc.

It is not working like nothing happens. It opens the "file" menu bar - but i dont want it to open this menu. ^.^

---

### Post by gordintoronto on 2011-12-23
I see the same result when I run MC and press F10. If I mouse to MC's "file" and click on Exit, that works.

---

### Post by phil9r on 2011-12-24
Thanks for your help.

So there is NO possibility of disabling the F10 Key and use it for the MC only ... ?

---

### Post by gordintoronto on 2011-12-24
Sorry, I don't know for sure. Perhaps something could be done in Terminal's settings.

---

### Post by ray field on 2012-04-04
this is really silly. there must be a way to disable F10 calling up the menu in a menu profile.

---

### Post by isecore on 2012-05-11
Somewhat old thread, sorry for waking it, but I'm also going nuts.

I work a lot in various shells, and I use MC a lot as well. I recently upgraded to 12.04 and now every time I press F10 it insists on displaying the right-click menu from the mouse. It's driving me insane, and I've found nowhere to disable it. I need all my F-keys to be unbound from all functions.

Help!

---

### Post by MrDamian on 2012-05-12
> **isecore said:**
> Somewhat old thread, sorry for waking it, but I'm also going nuts.

I work a lot in various shells, and I use MC a lot as well. I recently upgraded to 12.04 and now every time I press F10 it insists on displaying the right-click menu from the mouse. It's driving me insane, and I've found nowhere to disable it. I need all my F-keys to be unbound from all functions.

Help!
create ~/.config/gtk-3.0/gtk.css

@binding-set NoKeyboardNavigation {
unbind “<shift>F10&#8243;
}
* {
gtk-key-bindings: NoKeyboardNavigation
}

---

### Post by isecore on 2012-05-13
> **MrDamian said:**
> create ~/.config/gtk-3.0/gtk.css

@binding-set NoKeyboardNavigation {
unbind “<shift>F10&#8243;
}
* {
gtk-key-bindings: NoKeyboardNavigation
}

Nope, didn't do the trick. Thanks for trying, though. Appreciate it!

---

### Post by PaulW2U on 2012-05-13
Luckily I  don't have that problem with konsole in Kubuntu, F10 works perfectly.

But I seem to remember when running an earlier version of Ubuntu I added some keyboard shortcuts to mc. I think I made F12 work as F10 by editing one of mc's config files.

Something to try?

---

