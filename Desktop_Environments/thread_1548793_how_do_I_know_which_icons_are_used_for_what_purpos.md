---
title: "how do I know which icons are used for what purpose?"
date: 2010-08-08
forum: Desktop Environments
---

### Post by miesogeno on 2010-08-08
i'm trying to create an icon theme, but i don't want to replace the wrong icons. some of them look the same but are used for different situations like status, apps, toolbars, and the categories folders are not always intuitive.

is there any "map" on icon usage by the system or aplications?
or is there any way of knowing where a particular icon is being "fetched" from at a given moment?

---

### Post by pastalavista on 2010-08-08
...

---

### Post by miesogeno on 2010-08-08
?

---

### Post by slooksterpsv on 2010-08-08
Where are you looking at the icons at? /usr/share/icons - or in Appearance?

If you tell us the name, we can help you out. But we're going to need further information on what icons, where you found them at, etc.

---

### Post by miesogeno on 2010-08-09
oh, thanks, I know where the icons are.

but I'm making a icon theme. there are hundreds of icons in a theme and I'm not changing them all. I just wanted to change the most commonly used.

an example:

in some themes, in the "action" folder, you have "**system-shutdown.png**" and "**system-shutdown-panel.png**". they look the same, often one is a simlink of the other. but one is intended to show in the panel, and the other, to show in some other popup warning windows or something.

so, what I wanted to know is if there is guide of the icons used per application or action or something, or if there is a way to click on an icon (on start menu, for instance) to know where the system is getting it from.

---

### Post by ABCC on 2010-08-09
You could have a look in /usr/share/applications/desktop.en_US.utf8.cache

---

### Post by miesogeno on 2010-08-14
thank you. that's the closest to what i wanted!

but... thats only for application icons, and in my particular case, I was trying to change especially the toolbar icons, panel icons, status icons, stock, etc. those are the ones i'm having a little trouble to find.

i was looking for a list (or more) like the one you showed me to, but for all of the icons.

---

### Post by ABCC on 2010-08-14
Maybe this will come in handy?

[http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html#names](http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html#names)

---

### Post by miesogeno on 2010-08-14
aha! thats it!! :D


thank you so much!

---

