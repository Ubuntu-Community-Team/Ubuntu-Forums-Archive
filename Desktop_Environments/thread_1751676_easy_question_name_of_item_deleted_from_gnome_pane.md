---
title: "easy question: name of item deleted from gnome panel, please?"
date: 2011-05-06
forum: Desktop Environments
---

### Post by gregconquest on 2011-05-06
I was trying to get more real estate up top, so I tried to delete one unused item and three more disappeared with it. now when I try "Add To Panel", the item I deleted is not there.

Here it is:
[IMG]http://image.bayimg.com/jahchaadp.jpg[/IMG]
keyboard - network - sound - unused envelope

The last one is what I was trying to delete.

Can anyone tell me how to revive this area of my panel?

I once removed the far-right shutdown button from another PC. I couldn't figure out how to bring it back either. Why is this so hard? Built-in apps there should be the easiest to find and manipulate.

Thanks,
Greg

---

### Post by wilee-nilee on 2011-05-06
> **gregconquest said:**
> I was trying to get more real estate up top, so I tried to delete one unused item and three more disappeared with it. now when I try "Add To Panel", the item I deleted is not there.

Here it is:
[IMG]http://image.bayimg.com/jahchaadp.jpg[/IMG]
keyboard - network - sound - unused envelope

The last one is what I was trying to delete.

Can anyone tell me how to revive this area of my panel?

I once removed the far-right shutdown button from another PC. I couldn't figure out how to bring it back either. Why is this so hard? Built-in apps there should be the easiest to find and manipulate.

Thanks,
Greg

notification in the add to panel search.

---

### Post by ChipOManiac on 2011-05-06
Indicator Applet...

---

### Post by Copper Bezel on 2011-05-06
Yes, all those items are simply appearing in the indicator applet half of the system tray, which is more or less passive. Since the Classic desktop doesn't have a blacklist for indicators, to get rid of the e-mail icon, you'll need to uninstall it.

```
sudo apt-get remove indicator-messages
```

---

### Post by gregconquest on 2011-05-07
Thanks Chip and Copper. Your answers were right, and my indicator app is now back and slimmed down even :-)

Wilee, your answer was almost right, and I was able to undo what you suggested ;-)

---

