---
title: "Can we assign custom icons in UNR?"
date: 2010-02-27
forum: Desktop Environments
---

### Post by icthis3t7 on 2010-02-27
After falling in love with Ubuntu 9.10 and realizing that my Windows 7 RC was going to stop working in 3 days, I decided that I would go all in for Ubuntu. :D

So, I've recently installed UNR 9.10 for my MSI Wind U100. Yes, I have the screen flicker, but only on the login and I can halfway deal with that. I never use a webcam so no worries with that not working. No USB issues for me either, so overall I'm quite happy with this new design.

Except for one thing.

Seeing as this is not your usual desktop, one cannot simply 'right-click' an icon and edit some of its details, such as a custom icon. I am a HUGE fan of Google Chrome, so of course I use it as my primary web browser. However, there is one small annoyance with this: their default icon resolution is too small, so when UNR scales it up, it gets all fuzzy. Not exactly the thing you would want to see on your crisp new OS ;)

So, basically the question is, how (or can you even) change a default icon in UNR? 

My trials:

I've been to
```
~/.gconf/apps/netbook-launcher/favorites/
```
and found the target of the Chrome link is:
```
/usr/local/share/applications
```
which has a link to the Chrome browser. After 'right-clicking' it, I am given an area to change its icon. I used a .png that was provided with the install at
```
/usr/local/share/icons/hicolor/256x256/apps
```
Even after a restart, the icon in the UNR desktop was the same.

I have done more, but that's what I would have called the "closest to maybe working" I've reached. Any ideas?

Thanks in advance :D

---

### Post by Arkitekt on 2010-02-27
Easiest way I know how to do it is to go to the System tab in the launcher, open up Main Menu, find the program you wish to edit the icon for, select it and open properties, click the icon image in the top left, and browse to the directory of the .png you wish to use and select it.

---

### Post by icthis3t7 on 2010-02-27
> **Arkitekt said:**
> Easiest way I know how to do it is to go to the System tab in the launcher, open up Main Menu, find the program you wish to edit the icon for, select it and open properties, click the icon image in the top left, and browse to the directory of the .png you wish to use and select it.

Hadn't thought about that..! After doing so, the icon is using the higher resolution, but only under the "Internet" tab. For some reason, whenever it is added to the "Favorites" tab, it gets the old, low-res icon.. ugh.

So, thoughts on this? :popcorn:

---

### Post by Arkitekt on 2010-02-27
restarting should refresh the link between the two.

I have changed the name of some of the programs and Favorites only reflects the change after restarting.

---

### Post by icthis3t7 on 2010-02-27
> **Arkitekt said:**
> restarting should refresh the link between the two.

I have changed the name of some of the programs and only after restarting does the same program under favorites reflect that change.

I did that, no success.

---

### Post by Arkitekt on 2010-02-27
ok, I think I have figured this out.

is the program in ~/.local/share/applications?

If so, right click it and go to properties and do the same thing for the icon on that one, that will change the icon in Favorites. If not, I wouldn't really know where to look.

there is a bug regarding the issue of changed icons not updating in the favorites [https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/424822](https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/424822)

---

### Post by icthis3t7 on 2010-02-27
Alright, you'll love this ;)

So, I had been using a 'system directory' (not like a common one such as 'Pictures' or something) because that's just where Google had them installed, and I didn't want to have to duplicate files if I didn't have to! So, I had already linked up the image via both the 'system>preferences>main menu' and under the '~/[yadayada]/applications' to link to that file. It didn't work.

Well guess what happens when you copy that image file, put it under the 'Pictures' folder and link both of those to that said directory? MAGIC! ;)

Well, this was all quite unnecessary (like not being able to organize your favorites!!), but at least there's a way to do it!

Thanks for your help! :D

---

### Post by Arkitekt on 2010-02-27
this is from another thread

[quote=jonest1]
1. Open up 'System Tools' -> 'Configuration Editor'
If it's not there, open alacarte as in a previous reply on this topic and add it in.

2. Open the configuration editor (aka gconf editor) and use with care. Navigate to apps -> netbook-launcher -> favorites and click on favorites.

3. In the right-side pane, double-click on the favorites_list item. You will then be able to move individual items up and down the list.

4. Close out of the configuration editor. You will need to logoff and log back in to see the changes. There is no need for a full restart.
[/quote]

---

