---
title: "I screwed up panels need help"
date: 2010-05-04
forum: Desktop Environments
---

### Post by joelw135 on 2010-05-04
I was playing around and I in error deleted both top and bottom panels. How do I get them back? I now can't get to the menus etc.

---

### Post by Nidwow on 2010-05-04
> **joelw135 said:**
> I was playing around and I in error deleted both top and bottom panels. How do I get them back? I now can't get to the menus etc.
 
 
Press ALT+F2 and in the run dialog box, type gnome-terminal then click run. 
 
 
Enter the following command at the prompt:
```
gconftool-2 &#8211;-shutdown
gconftool &#8211;-recursive-unset /apps/panel
``` 
 
(*[SIZE=2]no spaces between the two dashes before shutdownno spaces between the two dashes before shutdown)[/SIZE]*
 
Then enter the next command:
```
rm -rf ~/.gconf/apps/panel
```
 
 
And enter one more command:
```
pkill gnome-panel
```
 
HTH

---

### Post by joelw135 on 2010-05-04
> **Nidwow said:**
> Press ALT+F2 and in the run dialog box, type gnome-terminal then click run. 
 
 
Enter the following command at the prompt:
```
gconftool-2 –-shutdown
gconftool –-recursive-unset /apps/panel
``` 
 
(*[SIZE=2]no spaces between the two dashes before shutdownno spaces between the two dashes before shutdown)[/SIZE]*
 
Then enter the next command:
```
rm -rf ~/.gconf/apps/panel
```
 
 
And enter one more command:
```
pkill gnome-panel
```
 
HTH

I did that and lost my theme and all the icons I had set on my desktop.

---

### Post by Nidwow on 2010-05-04
> **joelw135 said:**
> I did that and lost my theme and all the icons I had set on my desktop.
 
Did you get two gnome panels back to default top, bottom and menus?  Stuffs that you put on panel prior will be lost at the time of your acidentally deleting the panels.
 
Before you have restore the gnome panel back to the default setting you still have stuffs on your desktop?  Restoring gnome panel shouldn't effect desktop items anyhow.

---

### Post by joelw135 on 2010-05-04
> **Nidwow said:**
> Did you get two gnome panels back to default top, bottom and menus?  Stuffs that you put on panel prior will be lost at the time of your acidentally deleting the panels.
 
Before you have restore the gnome panel back to the default setting you still have stuffs on your desktop?  Restoring gnome panel shouldn't effect desktop items anyhow.

OK I will have to figure out why it is all screwed up. I do have the default panels. Thanks.

---

