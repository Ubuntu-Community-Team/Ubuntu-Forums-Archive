---
title: "Make menus semi-transprent"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by DrQuincy on 2007-04-22
I'm on Ubuntu Feisty running XGL / Beryl.  Can I make my menus semi-transparent?  You could do it in KDE without 3D accelleration - can you do it either way in Gnome?

---

### Post by raul_ on 2007-04-22
[http://www.beryl-project.org/faq.php#ub4]("http://www.beryl-project.org/faq.php#ub4")

---

### Post by notwen on 2007-04-22
>  I really want transparent menus!
    You are going to learn how to use the state plugin really quick then. Let's open up beryl-settings again, and navigate to Set Window Attribs -> String Lists. In here you will see lists (probably all blank) where you can inpute values. We need to add values to the Window Opacity list. Click the add button, and a new entry will appear, click on the entry to edit. Change it to read w:DropdownMenu:90. The "w" means we are going to define the window type in the next feild, the "DropdownMenu" is the window type, and the "90" is the level of opacity. You need to also add w:Menu:90 and w:PopupMenu:90 to complete the look.

Just wanting to clarify, this tweak in beryl makes applications menus transparent in applications, but does this make the menus under the gnome panel transparent as well?  I've been wanting transparent gnome menus for ages.

---

### Post by raul_ on 2007-04-22
Try it and see for yourself :)

---

### Post by notwen on 2007-04-22
Thanks a ton, it sure beats trying different gtkrc settings over and over.   I'll have to play w/ the windows stuff more, but for now my transparent gnome menus rock. Thanks again. =]

---

### Post by Ender Black on 2007-04-22
Alright... darn it... 

I followed the tut to a "T" and I can't get my dropdown menus to become transparent.  I even set the opacity to 25% just to make sure I was seeing effect.  w:DropdownMenu:xx where xx is the percentage of opacity isn't working for me.  Any ideas?  ](*,)

---

### Post by FuturePilot on 2007-04-22
It's not working for me either:confused:

---

### Post by yodaky on 2007-04-22
if you dont mind the gnome panel/taskbar being transparent too then you can do:

```
c:Gnome-panel:85
```

---

### Post by FuturePilot on 2007-04-22
> **yodaky said:**
> if you dont mind the gnome panel/taskbar being transparent too then you can do:

```
c:Gnome-panel:85
```

Wow! That's awesome! But I still can't get any transparent menus in applications.
Is there any way to make the terminal semi-transparent with this plugin?

---

### Post by yodaky on 2007-04-22
im still new to beryl so i am finding things out while i go so i cant help much with the dropdown transparency.  however, the terminal transparency would be:

```
c:Gnome-terminal:85
```

---

### Post by rocknrolf77 on 2007-04-22
Lookin' good now  Thanks :)

---

### Post by chakkaradeep on 2007-04-22
> **raul_ said:**
> [http://www.beryl-project.org/faq.php#ub4]("http://www.beryl-project.org/faq.php#ub4")

I cant find this 
**Let's open up beryl-settings again, and navigate to Set Window Attribs -> String Lists** :(

---

### Post by rocknrolf77 on 2007-04-22
Window managment > set window attribs by various criteria > window opacity

---

### Post by FuturePilot on 2007-04-23
This might help;-)

---

### Post by chakkaradeep on 2007-04-23
> **FuturePilot said:**
> This might help;-)

Thanks !

Its really nice to see all these 3d Effects in my Machine ! Vista said it does not support my graphics driver , and i just dont know for what reason !

---

### Post by DrQuincy on 2007-04-23
> **rocknrolf77 said:**
> Window managment > set window attribs by various criteria > window opacity

I don't have that option; I have "Set Window attribus by various criteria" but there is no Strings options - any ideas?

---

