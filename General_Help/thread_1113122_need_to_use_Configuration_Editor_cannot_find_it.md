---
title: "need to use Configuration Editor cannot find it"
date: 2009-04-01
forum: General Help
---

### Post by workshop1702 on 2009-04-01
hi i need to use the config editor i have checked and it is installed but i cannot find it , my other pc has it listed in aplications accesories.
it isnt  listed on my other machine , anyone any idea how i can get it on this machine please.

---

### Post by Steve1961 on 2009-04-01
Right click the applications menu on the top panel and select edit menu.  Then make sure there's a tick for the configuration editor under the system tools menu

---

### Post by pbpersson on 2009-04-01
Are you referring to this package?

```
An editor for the GConf configuration system
GConf-Editor is a tool used for editing the GConf configuration database.
This is not the recommended way of setting desktop preferences, but it might
be useful when the proper configuration utility for some software provides
no way of changing some option
```

---

### Post by coffeecat on 2009-04-01
Go to System > Preferences > Main Menu. On the left, click on System Tools, and tick Configuration Editor in the middle pane.

System Tools is where it usually appears, so I'm surprised your other machine has it in Accessories.

---

### Post by fooman on 2009-04-01
have a look in applications > system tools

or,  just open a terminal (applications > accessories > terminal) and type:

```
gconf-editor
```

then press enter.

hope that helps.

---

### Post by pbpersson on 2009-04-01
<rant>

If I have software installed on my machine, why is is being hidden from me in the menus so I do not even know it is there????

</rant>

---

### Post by coffeecat on 2009-04-01
> **pbpersson said:**
> <rant>

Because you can do a **lot** of damage with it if you are inexperienced or even in a bad mood. :wink:

Besides, inexperienced users don't need it and experienced users either know how to activate it or they know where to ask. :p

---

### Post by issih on 2009-04-01
Its the same thing as MS not letting you know that registry editor is lurking in there...its a powerful tool, and you shouldn't be messing with it unless you are sure.

Either way, its not hidden, its right there in the menu editor :)

---

### Post by pbpersson on 2009-04-01
Well.....I suppose.....but I have been installing all this software and it has been vanishing into a black hole.  It was very annoying.  ;)

---

### Post by issih on 2009-04-02
If you want to know where things have been installed, navigate to the package in question in synaptic, select it, and then look at its properties...in there is a list of installed files.

That way you can find out where they are hiding.

Hope that helps

---

