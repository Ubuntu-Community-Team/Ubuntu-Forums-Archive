---
title: "How to Change the Gnome Menu Icon?"
date: 2010-01-22
forum: Desktop Environments
---

### Post by Stigmata13 on 2010-01-22
Hello everybody. I'm pretty new to Ubuntu, and I was wondering how I would go about changing the default Ubuntu start menu button to something specific.
I would like to use this image: [http://i848.photobucket.com/albums/ab41/demonsoul09/Skull_glove1.jpg](http://i848.photobucket.com/albums/ab41/demonsoul09/Skull_glove1.jpg)
As the icon for the start menu, but I wouldn't know about how to go about doing so. Does anyone have any advice?
Thanks  in advance.

---

### Post by eamon63 on 2010-01-22
[http://www.google.com.ph/search?q=How+to+Change+the+Gnome+Menu+Icon%3F&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com.ph/search?q=How+to+Change+the+Gnome+Menu+Icon%3F&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by phillychease on 2010-01-22
go download ubuntu tweak. i think theres an option so you can change it

---

### Post by NormanFLinux on 2010-02-08
Ubuntu Tweak's option doesn't work in Karmic. In other words, when you choose a custom icon, it always reverts back to the default icon after respawning and there is no way to force a change to stick.

---

### Post by TheNessus on 2010-02-08
> **NormanFLinux said:**
> Ubuntu Tweak's option doesn't work in Karmic. In other words, when you choose a custom icon, it always reverts back to the default icon after respawning and there is no way to force a change to stick.

Just remove the gnome menu icon in your icon theme and replace it with another icon of your choosing. it's in .themes in your home directory. the replacement has to have the same name as the original, of course. It will work 100%. It may require terminal use.

---

### Post by NormanFLinux on 2010-02-08
Changed all the icons. It still didn't change to the custom icon I chose. Ubuntu Tweak can't make it stick.

---

### Post by psbrogna on 2010-10-24
This is how I change my start menu icon:

$ gconf-editor

Check the following keys:

/apps/panel/objects/object_4/custom_icon
/apps/panel/objects/object_4/use_custom_icon

Note: Yours might not be object_4, check the other objects looking for the one that's your menu.

Cheers,
- Philip

---

