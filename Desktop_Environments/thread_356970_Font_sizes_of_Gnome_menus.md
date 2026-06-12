---
title: "Font sizes of Gnome menus"
date: 2007-02-09
forum: Desktop Environments
---

### Post by grado on 2007-02-09
Hi, I have really big and ugly font sizes for my Gnome menu and all GTK applications (firefox included). Whatever I configure as the font size does not seem to matter. Pls see screenshots.

Is it possible to reduce font sizes we see in Gnome toolbar, menus, and other GTK application?

Thank you!

PS: 2.6.17-10-386 with Ubuntu/Beryl

---

### Post by alphane on 2007-02-09
Wow, that does seem huge!

I only have things this large when I'm outing the video to my TV to watch ill-gotten movies!

Anyhoo, on your second attachment within your font options, there is a details button.

Give that a quick click and change the DPI setting to say around 80 (that's what I use anyway).

This will reduce your font size, and regain some of your desktop space.

A quick restart/logout-login may be required for the fonts to appear correctly on all programs.

Hope this helps.

---

### Post by grado on 2007-02-09
Changing DPI settings didn't help. But thanks for the suggestion.

Anything else that can be done?

---

### Post by ComplexNumber on 2007-02-09
[B]grado
[/B]whats the name of the gtk theme that you're using?

---

### Post by grado on 2007-02-09
I think it is called mist. Is this the theme we set in System > Preferences > Theme?

---

### Post by corstar on 2007-02-09
Have you tried System>Preferences>Fonts

Customize it to whatever you like.
I love having freesans for most things

---

### Post by grado on 2007-02-09
System>Preferences>Fonts doesn't seem to affect Gnome menus and GTK applications :(
my first post in this thread also has a screenshot for this.

---

### Post by ComplexNumber on 2007-02-10
so anything you change in fonts has NO effect whatsoever, right? that seems really really odd. are you running fonts as root (ie with sudo)?
my fonts are smaller than yours and i've got mine set to 10 rather than 8.

---

### Post by grado on 2007-02-10
Thats right! I am not sure how this thing works, but may be this has something with Beryl. Any theme/font change I am making is not being applied.

IMHO, we don't need to set fonts as root because font and other window-manager properties are user specific.

Anyone else having similar issues?

---

### Post by ComplexNumber on 2007-02-10
EDIT: i was mistaken.

---

### Post by mcduck on 2007-02-10
> **grado said:**
> Thats right! I am not sure how this thing works, but may be this has something with Beryl. Any theme/font change I am making is not being applied.


Try running 'gnome-settings-daemon &' in a terminal. If that helps add it to your session in System/Preferences/Session.

---

### Post by grado on 2007-02-10
Wow! That finally does the job. Been struggling for days with this problem. Thanks a ton for that. If you're in Baltimore I will get you a beer :)

Just interested in knowing what is this thing. Could you pls point me to some document etc?

---

### Post by mcduck on 2007-02-11
> **grado said:**
> Wow! That finally does the job. Been struggling for days with this problem. Thanks a ton for that. If you're in Baltimore I will get you a beer :)

Just interested in knowing what is this thing. Could you pls point me to some document etc?
Thanks, but I'm currently in Denmark, and there's more beer than even I can drink ;)

Anyway, I'm not sure what's the cause for gnome-settings-daemon not starting with Beryl, but I had the same problem when I updated to Edgy & reinstalled Beryl, and I found this solution from Beryl forums.

It seems to fix the problem and causes no new troubles so I didn't do any more research about it. :)

---

