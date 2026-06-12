---
title: "fluxbox menu icons on the right and on the title*"
date: 2009-08-16
forum: Desktop Environments
---

### Post by withoutn on 2009-08-16
Hello people,
It seems at least in my current fluxbox configuration that menu icons are by default placed on the left of an entry. How can i placed them on the right instead?

Also, it looks like any icon declaration placed in the title (where it says fluxbox -v by default) is ignored. How can i put an icon there next to the title? Or even an icon itself without the title. 

Thanks in advance.

---

### Post by ve4cib on 2009-08-16
Not sure about the menu, but for the window title there are two lines in ~/.fluxbox/init that you will want to change:

```

session.screen0.titlebar.left:  Stick MenuIcon
session.screen0.titlebar.right: Shade Minimize Maximize Close

```

Both are ordered lists of what should be placed on the titlebar.  The .left one starts at the left-hand edge and goes to the right.  The .right one starts after the .left, and keeps going to the right (with the last element lined up on the right-hand edge of the titlebar).

So if all you want on your titlebar is the sticky button on the left and the icon on the right you would have:

```

session.screen0.titlebar.left:  Stick
session.screen0.titlebar.right: MenuIcon

```

There's more information [here](http://fluxbox-wiki.org/index.php?title=Editing_the_init_file) that you might find useful for configuring Fluxbox.

---

### Post by withoutn on 2009-08-16
hello, thanks for your post however i really dont care about anything else besides icons on the right in the menu and an icon in the title* in the menu where it says fluxbox -v. 

I think there might have been some misunderstanding. Im not looking for customization of a titlebar but the _title_in_the_menu where it says fluxbox.

If anybody knows, please gimme a tab,

Thanks in advance

---

### Post by RedSquirrel on 2009-08-16
> **withoutn said:**
> Hello people,
It seems at least in my current fluxbox configuration that menu icons are by default placed on the left of an entry. How can i placed them on the right instead?

Also, it looks like any icon declaration placed in the title (where it says fluxbox -v by default) is ignored. How can i put an icon there next to the title? Or even an icon itself without the title.
As far as I know, it is not possible to achieve these goals with fluxbox. You would have to modify the fluxbox source code to add those features.

---

