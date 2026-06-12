---
title: "Mint Style Gnome Menu?"
date: 2010-08-12
forum: Desktop Environments
---

### Post by KdotJ on 2010-08-12
Hey, I really like the style of the gnome main menu that Linux Mint has on its gnome variant... openSUSE has the same style of menu. If you don't know what I mean, here is a link to a screenshot...

[LINK HERE]("http://techmiso.com/wp-content/uploads/2009/05/linux-mint-7-menu.jpg")

Does anyone know if it is possible to get this in Ubuntu? Rather then the usual list menu that comes as default?

Thanks

---

### Post by Wisp558 on 2010-08-12
Well, this is just a guess, but I bet you could find a .deb or theme package mint uses. Those sorts of things *should* be interchangeable. I doubt mint would write a whole new menu. Unfortunately, I'm not sure where those would be. Just google fuel.

---

### Post by ajgreeny on 2010-08-12
Yes, you can use the mint menu, but need to check which mint version's menu to use, because in the past they have not always coincided versions, mint to ubuntu.

You may also need another .deb package, mint-system, I think, but can't remember with any certainty.  I am sure there will be info elsewhere in this forum, and probably the mint forum with more details.  Once you know what you need you should download them manually and install with ```
sudo dpkg -i *
``` from the folder with the files in it, then add the mint menu from the panel right click "Add to panel"

---

### Post by KdotJ on 2010-08-12
Thanks for the replies guys, I'm googling as we type lol. It's a Shane ubuntu doesn't have this readily available, it looks very nice in my opinion

---

### Post by ajgreeny on 2010-08-12
Another thought suddenly came!

There is a package in the ubuntu repos called **gnome-main-menu** very like the mint-menu.

Have a look at that as well.

---

### Post by rollin on 2010-08-12
You could try the link here too, hopefully after some digging you might find the gnome-panel your looking for... [http://community.linuxmint.com/software](http://community.linuxmint.com/software)

---

### Post by ubunterooster on 2010-08-12
Gnome-main-menu, IMaO is not at all similar except that it has one open button instead of threee

---

### Post by ubunterooster on 2010-08-12
> **rollin said:**
> You could try the link here too, hopefully after some digging you might find the gnome-panel your looking for... [http://community.linuxmint.com/software](http://community.linuxmint.com/software)Found it.
[http://community.linuxmint.com/software/view/mintmenu](http://community.linuxmint.com/software/view/mintmenu)

---

### Post by rollin on 2010-08-12
> **ubunterooster said:**
> Found it.
[http://community.linuxmint.com/software/view/mintmenu](http://community.linuxmint.com/software/view/mintmenu)

Awesome, nice search-fu! Fingers crossed it works for OP :)

---

### Post by UberStudent on 2010-08-13
[http://www.geekconnection.org/remastersys/repository/karmic/mintmenu_4.9.4_all.deb](http://www.geekconnection.org/remastersys/repository/karmic/mintmenu_4.9.4_all.deb) is a debranded MintMenu.

---

### Post by UberStudent on 2010-08-13
BTW, Advance Gnome Menu [http://opendesktop.org/content/show.php/Advanced+Gnome+Menu?content=93791&PHPSESSID=1e6339d2ed69cd56b4c5f37eacc349b7](http://opendesktop.org/content/show.php/Advanced+Gnome+Menu?content=93791&PHPSESSID=1e6339d2ed69cd56b4c5f37eacc349b7) is visually pretty sharp and could be developed upon by the FOSS community. It's currently abandoned and a bit buggy.

---

### Post by TheWeakSleep on 2010-08-13
Sorry if it's a little late but the guys from webupd8 maintain a ppa

```
sudo add-apt-repository ppa:webupd8team/mintmenu && sudo apt-get update
```
```
sudo apt-get install mintmenu
```

---

### Post by ajgreeny on 2010-08-13
> **ubunterooster said:**
> Gnome-main-menu, IMaO is not at all similar except that it has one open button instead of threee
**Gnome-main-menu **is not the same as **main-menu**.  Look in the repos and you will see a description of both.  Main-menu is a single button simple menu, but gnome-main-menu is a slab type just like Mint or OpenSuse.

Try it; you'll see what I mean.

---

### Post by KdotJ on 2010-08-13
A massive thank you at all of you for your input. You guys have given me so many options and I'm rely grateful. Km not at home until later today but I will give them all a go :-) 

Thanks everyone

---

