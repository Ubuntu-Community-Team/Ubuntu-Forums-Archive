---
title: "[SOLVED] Animation effects on main menu"
date: 2008-12-10
forum: General Help
---

### Post by chamber on 2008-12-10
I was wondering if there was a way to add effects to the main menu so that when I click on appliactions or one of the sub menus in it it will open with the fold/razor/burn etc effect?

I think I remember seeing it in a youtube video.

Thanks muchly.

---

### Post by stinger30au on 2008-12-10
piece of cake

you need to add simple compiz settings manager

this is done by

sudo apt-get install simple-ccsm


once it has finished d/l and install click on

system
preferences
advanced desktop effects

and now select hollywood aint got nuffin
and have alook thru the tabs and set everything to random

presto!

---

### Post by ellalan on 2008-12-10
This is my Open Animation settings,you can take it as a guide and choose whatever setting you want.

---

### Post by Forlong on 2008-12-10
If you have already ccsm (compizconfig-settings-manager) installed, go to the **Animations** plugin and change the second value under **Open Animation**

It should have this Windw Match setting:
```
(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal)
```

Change **Fade** to anything you like.

---

### Post by eternalnewbee on 2008-12-10
> and now select hollywood aint got nuffin
A new plugin?

---

### Post by chamber on 2008-12-10
Thanks to all, 

I'll have a play about when I get home and away from windoze.

---

### Post by chamber on 2008-12-10
> **ellalan said:**
> This is my Open Animation settings,you can take it as a guide and choose whatever setting you want.

[QUOTE=Forlong]If you have already ccsm (compizconfig-settings-manager) installed, go to the Animations plugin and change the second value under Open Animation

It should have this Windw Match setting:
Code:

(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal)

Change Fade to anything you like. [/QUOTE]

Got it working using this.

Thanks to all!:guitar:

---

### Post by Forlong on 2008-12-15
> **eternalnewbee said:**
> A new plugin?
No, that's just a profile in simple-ccsm.

---

### Post by Khru on 2009-04-15
> **chamber said:**
> Got it working using this.

Thanks to all!:guitar:

This works really well. Thanks!

---

### Post by thongstele on 2010-05-31
> **chamber said:**
> I was wondering if there was a way to add effects to the main menu so that when I click on appliactions or one of the sub menus in it it will open with the fold/razor/burn etc effect?

I think I remember seeing it in a youtube video.

Thanks muchly.

I also want to make like what u said but I dont know how to. I watched the clip on Youtube on the following link: [http://www.youtube.com/watch?v=X6cQozuoS5I]("http://www.youtube.com/watch?v=X6cQozuoS5I")
Who knows to make Ubuntu have effects with menu like the begining of the clip, please show me. Ths so much!

---

### Post by chamber on 2010-06-17
> **Forlong said:**
> If you have already ccsm (compizconfig-settings-manager) installed, go to the **Animations** plugin and change the second value under **Open Animation**

It should have this Windw Match setting:
```
(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal)
```

Change **Fade** to anything you like.

This worked for me and should work for you.

---

