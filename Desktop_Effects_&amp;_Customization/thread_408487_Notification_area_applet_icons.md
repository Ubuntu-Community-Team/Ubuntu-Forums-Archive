---
title: "Notification area applet icons"
date: 2007-04-13
forum: Desktop Effects &amp; Customization
---

### Post by chemicalcomfort on 2007-04-13
I'd just like to say hi all this is my first post here.  I'm not exactly certain if this is the right place for this but i'm gonna try anyway.

I love gnome and ubuntu.  They work so magically and inuitively it's simply amazing.  I've pretty much got my desktop setup to my likings except for one little thing.  

It's the stupid Notifications Area Applet icons. [IMG]http://i145.photobucket.com/albums/r204/chemcomfort/notificationarea.jpg[/IMG]

I've searched high and low all across the internet all to no avail.  I tried grepping through my system to find the specific image files but i can't seem to find the right ones.

Any suggestions?

---

### Post by xopher on 2007-04-13
So what you want - is to change the icons of the apps in the tray?

A place to look would be /usr/share/appname, eg.

```
/usr/share/listen/img
```

You could probably add your custom icons to your icone theme too, so it'll override the default ones, and you won't need to replace them each time the application is updated.

---

### Post by chemicalcomfort on 2007-04-13
Thanks for the reply!

But I tried putting custom icons in the "/usr/share/[appname]/" folder and it didn't have any change.  I can't seem to find the folder for my custom icon theme either :(.  would they be somewhere other than "/usr/share/icons" ?

---

