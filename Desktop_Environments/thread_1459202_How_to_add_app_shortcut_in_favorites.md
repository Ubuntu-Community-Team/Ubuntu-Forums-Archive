---
title: "How to add app shortcut in favorites?"
date: 2010-04-21
forum: Desktop Environments
---

### Post by hrcariagajr on 2010-04-21
Hi All,

I have here an application located on my home directory and i want to add a shortcut to the Favorties, so when i lunch my application i don't need to go to the application directory. Is this possible? How? 

I've been googling this but i can't find any solution.. 


Any help would be very much appreciated..

---

### Post by _0R10N on 2010-04-21
Hi hrcariagajr! what are you looking for exactly? Do you want a..

a- shortcut in your desktop?
```

ln -s <your_command> <where_it_should_be_located/myshortcut>
chmod +x <where_it_should_be_located/myshortcut>
```
b- shortcut in your panel?
```
Right click on the menu and simply add a custom launcher
```
c-  command line shortcut?
```
$ vi myshortcut

#!/bin/bash
<your_command>

$ sudo mv myshortcut /sbin/myshortcut
```

Kind regards!

_0R10N >>

---

### Post by hrcariagajr on 2010-04-21
This is what i really wanted to do(please see attach file).

Thanks

---

### Post by _0R10N on 2010-04-22
Oh!!! screenlet/desklet favoritessss!!](*,) doh!!! Oh!!!

I'll investigate it! looks interesting!:guitar:

_0R10N >>

---

### Post by _0R10N on 2010-04-22
Excuse my incompetence, but I can't get with the screenlet.. could you tell me its name?:confused:

_0R10N >>

---

### Post by txauma on 2010-05-11
Could not find a better way to do it than this:

Go to System -> Main Menu. Create a new item in any group, e.g. Accessories, now your launcher should appear in the selected group. Right-click on it and "Add to favorites"

hope this helps :)

---

### Post by spydeyrch on 2010-05-11
> **_0R10N said:**
> Excuse my incompetence, but I can't get with the screenlet.. could you tell me its name?:confused:

_0R10N >>

Actually, I don't think that it is a screenlet. It appears to be the new ubuntu light. That is the new menu dock on the left. I may be wrong but I think that is what it is. :)

-Spydey :guitar:

---

### Post by fabounet on 2010-05-12
you could probably do it with any dock.
at least with GLX-Dock, there is a Shortcuts applet and a Quick-Browser applet which probably do what you want.

---

### Post by davec64 on 2010-05-12
Hi Guys,

This is the Netbook edition.

Have you tried clicking on the application and dragging it over the Favourites option?

That worked in previous versions. :)

---

### Post by hasana on 2010-07-24
> **txauma said:**
> Could not find a better way to do it than this:

Go to System -> Main Menu. Create a new item in any group, e.g. Accessories, now your launcher should appear in the selected group. Right-click on it and "Add to favorites"

hope this helps :)

Hello,
Thanks for this extremely useful post! I have managed to add ETM to my Accessories and Favourites. However, I added the ETM icon to the accessories application and I do see it in the Accessories panel. But, I don't see it in the Favourites panel. I do see the ETM application with the default square-with-cogs, but not the ETM logo and I cannot figure out how to get the logo to display in Favourites. The path to the logo in Accessories is the full path: /usr/local/lib/python2.6/dist-packages/etm-560-py2.6.egg/etm/etmlogo_128x128x32.png

Has anyone else seen this?
adil

---

### Post by BandD on 2010-07-25
If you hover your mouse over the ETM icon in the Accessories panel you will see a little + sign appear, click on the + sign and it will add it to the favorites panel.

---

