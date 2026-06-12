---
title: "Custom Notification Panel Area Gnome 11.04"
date: 2011-05-11
forum: Desktop Environments
---

### Post by MrGreen on 2011-05-11
I wish to have just wifi and clock in notification area in Gnome, but my search for an answer only turns up unity settings.

Do not need user shutdown or email icon in panel

Is it possible to remove them without removing the whole thing?

MrG

---

### Post by Krytarik on 2011-05-11
- You can remove the "Indicator Applet Session" from your panel, the session related items will then appear in the "System" menu. To do so, just right-click at it and choose "Remove From Panel".

- The mail envelope is part of the "Indicator Applet", which is also used by the Network Manager. So, you can't remove the applet itself from your panel if you want to retain the latter. But instead you can remove its package, "indicator-messages":
```
sudo apt-get purge indicator-messages
```The judgement if you need that one or not, is of course up to you. I myself find it very handy, as I use it with Thunderbird.

Greetings.

---

### Post by MrGreen on 2011-05-11
I would like network, mail and volume control [plus clock]

Thank you for your help

---

### Post by Frogs Hair on 2011-05-11
If you are in Classic Gnome you should be able to remove the applets you don't want by right clicking the icon / indicator and and selecting remove.

To add items right click the panel and select add to panel and choose from the menu .

---

### Post by MrGreen on 2011-05-12
I am running classic gnome but I can only remove all, can add clock but network applet seems to be missing from list.

---

### Post by MrGreen on 2011-05-12
[http://shortrecipes.blogspot.com/2011/04/ubuntu-1104-natty-narwhal-how-to-remove.html](http://shortrecipes.blogspot.com/2011/04/ubuntu-1104-natty-narwhal-how-to-remove.html)

This helped solve my problem, it removed the log out and user name plus mail icon

Nice!

---

### Post by Krytarik on 2011-05-12
So, you didn't read my previous post, fine.

But if you prefer to figure it on your own, why did you start this thread in the first place?

Or if you did indeed read my post, and didn't understand it, why didn't you just ask about it?

---

### Post by MrGreen on 2011-05-12
Did read you post and did thank you for your help

Merely posted link to possibly help others

---

### Post by fjgaude on 2011-05-12
> **MrGreen said:**
> Did read you post and did thank you for your help

Merely posted link to possibly help others

Thanks! The reason our OS is named what it is:

A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed. ~ Archbishop Desmond Tutu, 1999

---

