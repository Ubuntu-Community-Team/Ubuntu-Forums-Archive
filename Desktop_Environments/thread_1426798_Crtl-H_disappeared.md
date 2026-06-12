---
title: "Crtl-H disappeared"
date: 2010-03-10
forum: Desktop Environments
---

### Post by giuliano1969 on 2010-03-10
Hi.
browsing directory with  nautilus, the menu item "show hidden file", has lost the ctrl-h command.
It isn't dispayed close to the item, and of course it is not funciotioning if I press ctrl-h

How can I  get it back ?

---

### Post by mechro on 2010-03-10
What happens if you hover mouse cursor over View > Show Hidden Files and then press ctrl-h?

---

### Post by davidyoung on 2010-03-11
> **giuliano1969 said:**
> Hi.
browsing directory with  nautilus, the menu item "show hidden file", has lost the ctrl-h command.
It isn't dispayed close to the item, and of course it is not funciotioning if I press ctrl-h

How can I  get it back ?

I never meet this case

---

### Post by giuliano1969 on 2010-03-11
> **mechro said:**
> What happens if you hover mouse cursor over View > Show Hidden Files and then press ctrl-h?

thanks mechro,
I'm astonished ... following your hint and pressing ctrl-h while hovering  with the mouse cursor on the menu item, made the action "ctrl-h" **REAPPEARED**  in the menu !!
And of course now it works again!! Many thanks 
I didn't find this solution googling on the web.....

Please.... tell me more about this feature...
Is this way of changing action command,  a general feature of gnome programs or is it of Nautilus only ?

---

### Post by gamersblood on 2010-03-11
Now i learned somthing new thanx;)

---

### Post by mcduck on 2010-03-11
> **giuliano1969 said:**
> thanks mechro,
I'm astonished ... following your hint and pressing ctrl-h while hovering  with the mouse cursor on the menu item, made the action "ctrl-h" **REAPPEARED**  in the menu !!
And of course now it works again!! Many thanks 
I didn't find this solution googling on the web.....

Please.... tell me more about this feature...
Is this way of changing action command,  a general feature of gnome programs or is it of Nautilus only ?

It is a feature of Gnome, allowing users to set their own men accelerators in all Gnome applications. But it shouldn't be enabled by default and at least Ubuntu 9.10 doesn't even have the option in the menus any more so I'm quite amazed how you might have been able to accidentally enable it.. :o

Anyway, open gconf-editor, browse to *desktop/gnome/interface* and disable the "*can_change_accels*"-key to turn off this feature.

---

### Post by mechro on 2010-03-11
As mcduck says this feature shouldn't be enabled by default.

You can also enable/disable this feature from **System > Preferences > Appearance > Interface:** check/uncheck **Editable menu shortcut keys**

Edit... reread mcduck... perhaps this doesn't work in Karmic.

---

### Post by asmoore82 on 2010-03-11
> **mcduck said:**
> Anyway, open gconf-editor, browse to *desktop/gnome/interface* and disable the "*can_change_accels*"-key to turn off this feature.

Quoted for sheer excellence.

I never knew this - or if I did I sure had forgotten it.
Glad it's to be turned off by default as well :D.

---

