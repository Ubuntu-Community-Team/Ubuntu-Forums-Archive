---
title: "True Transparency in Nautilus."
date: 2010-08-25
forum: Desktop Environments
---

### Post by jeddycakes on 2010-08-25
Okay,

I know there are plenty of other posts about this option, but pretty much ALL of them (as far as I can tell) are at least 5-6 months old and even more.
It is strange that the community has been crying out for **[COLOR="DarkRed"]true background transparency in Nautilus[/COLOR]** for such a long time and yet nothing seems to be happening. This forum is a perfect place for the powers-that-be (e.g. the brainy sods who are able to build awesomeness such as ubuntu linux) to let the people know about things happening with the world of ubuntu and reply to requests placed. 

Such as transparent Nautilus backgrounds!

It is possible to effect transparency on your desktop using Compiz Config. People without this or who don't know what it is, try this code in terminal :

```

sudo apt-get install ccsm

```

I **WOULD NOT** recommend on some netbooks, as it can get a bit screwy; it did so on my wifes, most frustratingly so.

Anyway, back to topic. To enable transparency once installed, press alt and F2 then simply type 'ccsm'. You should end up with a screen looking like this :

[IMG]http://a.imageshack.us/img39/642/ccsmscreenshot.png[/IMG]

From here, navigate to 'Trailfocus' within 'Effects'. Then click on the 'Appearance' tab. Change Focused window to something like 95 % with all other values changed to 100%.
Voila! Slightly transparent windows. =D>

However, this is somewhat troublesome. The more observant of you will have noticed that **EVERYTHING** is now transparent. Thats right, all of your windows now see through.
Annoyingly, your whole browser is also see through, even the page that you are on. This is, to me, fairly irritating and not so easy on the eye. Although, your Nautilus windows now look quite snappy :)

[IMG]http://a.imageshack.us/img841/9097/nautilustransparencyexa.png[/IMG]

If any geniuses out there feel like tackling this then the community as a whole would, I dare say, be eternally grateful. 

Any ideas?

---

### Post by Cant on 2010-08-25
I second this.

---

### Post by jeddycakes on 2010-08-30
Booooooo

I expected a bit more activity on this! I thought everyone wanted this lol...

---

### Post by Frogs Hair on 2010-08-30
I tried Elementary Nautilus and it looks like your picture :( . If I wanted full transparency I would switch to KDE and use some of the Emerald and Plasma themes . I tried some of emerald themes in 9.10 and 10.04 , but it seemed a bit of waste of resources just to get transparent window borders. I am not a developer so I have to wait until it becomes possible.

---

### Post by lusguz on 2010-09-29
I, too, would like to see "True Transparency". In the interim, I'm using a "cheap trick": I copied my desktop background to the usr/share/nautilus/patterns folder, then set it as my window background.  It isn't as good as "True Transparency", but it's the simplest thing you can do that comes close.

---

### Post by Cpierce on 2010-09-30
I don't know if this is what you guys are looking for, but this is what I have done. In ccsm check the Opacity,Brightness,and Saturation. Then double click on it so you can change the settings. In the "window specific settings" area, click on new, then type in "class=Nautilus" and adjust the slider to 85. That should get you a transparent nautilus. If you want a transparent terminal, click on new again and add "class=Gnome-terminal" and move the slider to 85 again. If you want the dropdown menus transparent, hit new again and enter " Tooltip | Menu | PopupMenu | DropdownMenu" and adjust to 85 again. Some people like the setting to be on 90 instead of 85, but you can adjust it where you like. You could enter all three commands in one line, but having three separate ones so you can adjust them independently is nice.

Hope this helps.

---

### Post by jeddycakes on 2010-10-02
> **Cpierce said:**
> I don't know if this is what you guys are looking for, but this is what I have done. In ccsm check the Opacity,Brightness,and Saturation. Then double click on it so you can change the settings. In the "window specific settings" area, click on new, then type in "class=Nautilus" and adjust the slider to 85. That should get you a transparent nautilus. If you want a transparent terminal, click on new again and add "class=Gnome-terminal" and move the slider to 85 again. If you want the dropdown menus transparent, hit new again and enter " Tooltip | Menu | PopupMenu | DropdownMenu" and adjust to 85 again. Some people like the setting to be on 90 instead of 85, but you can adjust it where you like. You could enter all three commands in one line, but having three separate ones so you can adjust them independently is nice.

Hope this helps.

Thanks for the input dude, However this tip just enables the same type of transparency as my method (although this method is WAY better)

What I wish to achieve is to have the windows box (the one with all the folders/files etc in) as transparent with the windows border remaining completely opaque. I probably didn't make that totally clear in the original post on this...um, post.

Thanks for your help though mate, its much appreciated :guitar:

---

### Post by hrickh on 2010-10-02
I've not tried all possible combinations, but Compiz is really quite deep in what it can do.

In addition to using "class=", there are also the type, name ID and role options.

You may want to play around with adding rules for any of those within the opacity, brightness and saturation settings.

Personally, I've been able to get wildly different settings for separate applications and their tooltips, secondary windows, etc.

R.
==

---

### Post by jeddycakes on 2010-10-06
> **hrickh said:**
> I've not tried all possible combinations, but Compiz is really quite deep in what it can do.

In addition to using "class=", there are also the type, name ID and role options.

You may want to play around with adding rules for any of those within the opacity, brightness and saturation settings.

Personally, I've been able to get wildly different settings for separate applications and their tooltips, secondary windows, etc.

R.
==

Care to share any methods you apply? Thanks for the input BTW

---

### Post by hrickh on 2010-10-06
> **jeddycakes said:**
> Care to share any methods you apply? Thanks for the input BTW
Well, some of what I do is set opacity differently for different applications.

Tooltips = 90
Gnome-panel = 86
Pidgin = 80
Tomboy = 80
AWN = 80
Weather within AWN = 75
file-browser-launcher within AWN = 80

and etc.

I've also set my window decorations to show some opacity.

As far as some of the other wiz-bang stuff, it's easy-come, easy-go. Personally, I can't stand the wobble effect, water, blur, Cube and similar stuff.

R.
==

---

