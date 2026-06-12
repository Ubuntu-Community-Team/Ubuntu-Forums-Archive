---
title: "Odd Gnome menu bug"
date: 2010-09-30
forum: Desktop Environments
---

### Post by quisnox on 2010-09-30
Currently using Ubuntu 10.04 with Gnome environment and have strange bug with my menu. Here are a lot of apps installed, but I CANT ACCESS all of them. Menu won't scroll down enough! When I'm trying to click something from down-side menu, it automatically rolls-up to default position:

[img]http://img837.imageshack.us/img837/9364/screenshotaq.png[/img]

So, only one way to run app from "deeper menu" is pressing alt+f2.

How can I fix that?


p.s. I'm really sorry, my English isnt good, but I think you will understand me.

---

### Post by coffeecat on 2010-09-30
If you hover your mouse pointer over the little down arrow at the bottom - the one you have ringed in red in your screeshot - the whole menu should scroll up to show you the last few menu entries. Hover the mouse pointer - don't click anything - and the menu should scroll. Then you can click on whichever entry you want. Or you can go to the top of the screen and hover over the up arrow and the menu will scroll back to its default position.

This is what is happening for me in Maverick/10.10. It should be the same in Lucid/10.04.

**Edit:** I've now booted into 10.04, and the menu is behaving correctly for me in 10.04 as well. I've added some menu entries to the Accessories menu and the menu scrolls if I move the mouse over the little down arrow. In fact, I can move the mouse pointer into the area to the side of the down arrow and that causes the menu to scroll just as well.

If this is what you are doing and it doesn't work for you then I don't know what to suggest.

---

### Post by quisnox on 2010-10-01
I don't know why but I can click any of icons :( When I;m trying to do that, menu quickly scrolls back to its previous position automatically.

---

### Post by stinkeye on 2010-10-01
> **quisnox said:**
> I don't know why but I can click any of icons :( When I;m trying to do that, menu quickly scrolls back to its previous position automatically.

I've had this problem before.
You can either,
Right click  on your main menu > edit menus
and untick some of the programs you rarely use

or

install gnome-color-chooser which will allow you to reduce the font size
and distance between entries.

I very rarely use the main menu and just use kupfer to start programs.
gnome-color-chooser is available in the software centre.

To install kupfer you need to add it's repository.

To add the repository and update your sources.
In the terminal...
```
sudo add-apt-repository ppa:kupfer-team/ppa && sudo apt-get update
```

To install kupfer.
```
sudo apt-get install kupfer
```

---

### Post by coffeecat on 2010-10-01
One other thing you could do, but it would be very fiddly. In edit menus you can create menus in the Accessories menu. With so many apps in the accessories menu you might want to think of creating 2-3 submenus and then having all your application launchers in the submenus. You could sub-categorise them that way and that would stop so many menu entries spilling off the bottom of the screen.

One big disadvantage to this though. I can find no way of moving a menu entry in edit menus. Which would mean you would have to create each and every new menu entry by hand and then delete the old ones - one by one. *Very* tedious.

---

