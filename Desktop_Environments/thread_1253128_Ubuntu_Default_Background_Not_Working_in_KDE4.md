---
title: "Ubuntu Default Background Not Working in KDE4"
date: 2009-08-29
forum: Desktop Environments
---

### Post by Tiwanaku on 2009-08-29
I like KDE, but I also like Ubuntu's default background.  Unfortunately, they do not seem to mix.

Here is a link to the background .PNG, which displays just fine in Firefox, the GIMP, and GTK+ apps in general:
 [[IMG]http://img42.imageshack.us/img42/6749/wartyfinalubuntu.th.jpg[/IMG]]("http://img42.imageshack.us/i/wartyfinalubuntu.jpg/")

Here is a link to how the image looks when selected as KDE4's background image (yes, almost no relation to the original PNG):
[[IMG]http://img143.imageshack.us/img143/3949/kde4desktopwithubuntude.th.png[/IMG]]("http://img143.imageshack.us/i/kde4desktopwithubuntude.png/")

To show how KDE cannot handle it at all, notice how it doesn't get a thumbnail in Dolphin:
 _[[IMG]http://img53.imageshack.us/img53/4592/dolphinoddity.th.png[/IMG]]("http://img53.imageshack.us/i/dolphinoddity.png/")_

This isn't a general problem; most PNG's work just fine in KDE, as also shown in Dolphin.  So what is it that's so different about the Ubuntu default GNOME background that it's giving KDE such trouble?

---

### Post by szadek_ on 2009-08-29
> **Tiwanaku said:**
> I like KDE, but I also like Ubuntu's default background.  Unfortunately, they do not seem to mix.

Here is a link to the background .PNG, which displays just fine in Firefox, the GIMP, and GTK+ apps in general:
 [[IMG]http://img42.imageshack.us/img42/6749/wartyfinalubuntu.th.jpg[/IMG]]("http://img42.imageshack.us/i/wartyfinalubuntu.jpg/")

Here is a link to how the image looks when selected as KDE4's background image (yes, almost no relation to the original PNG):
[[IMG]http://img143.imageshack.us/img143/3949/kde4desktopwithubuntude.th.png[/IMG]]("http://img143.imageshack.us/i/kde4desktopwithubuntude.png/")

To show how KDE cannot handle it at all, notice how it doesn't get a thumbnail in Dolphin:
 _[[IMG]http://img53.imageshack.us/img53/4592/dolphinoddity.th.png[/IMG]]("http://img53.imageshack.us/i/dolphinoddity.png/")_

This isn't a general problem; most PNG's work just fine in KDE, as also shown in Dolphin.  So what is it that's so different about the Ubuntu default GNOME background that it's giving KDE such trouble?


Just go to /usr/share/backgrounds/ , here you can find wht you are looking for , just copy the background you want to /home/placeyouwant , and then , choose from the desktop settings dialog .Have fun =)

---

### Post by Tiwanaku on 2009-08-29
> **szadek_ said:**
> Just go to /usr/share/backgrounds/ , here you can find wht you are looking for , just copy the background you want to /home/placeyouwant , and then , choose from the desktop settings dialog .Have fun =)

You don't understand.  Look at the .PNG file that is Ubuntu's default background in GNOME in Firefox or the GIMP, and you get the first picture.  Use ***the exact same .PNG file*** as KDE4's background image, and you get the second picture.  Make more sense what the problem is now?

---

### Post by krazyd on 2009-08-31
Could be that file is slightly corrupted, and KDE can't load it. Either download it again, or open it in GIMP and save it as a new PNG.

---

