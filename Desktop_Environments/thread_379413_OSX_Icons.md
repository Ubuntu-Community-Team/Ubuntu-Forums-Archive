---
title: "OSX Icons"
date: 2007-03-08
forum: Desktop Environments
---

### Post by th3gh05t on 2007-03-08
Hi,

I downloaded the OSX icons from this website, ([http://nekohayo.googlepages.com/icons)](http://nekohayo.googlepages.com/icons)), and installed them via the "Theme" area.

However, it doesn't change all of my applications to reflect all of the icons that came with the pack.

When I right-click on an application, (one that is in my panel), I go to Properties, and then click on the icon image.

I navigate to the folder (/home/user/.icons/OSX/scable/apps/) and there are bunch of .png icons in there, but they don't show up.

Why is this and how do I choose any icon I want?

Thanks for your time!

th3gh05t

---

### Post by th3gh05t on 2007-03-09
Well, I figured this out!

You have to add the application to your Desktop first, change the icon, and then add it to your panel.

It doesn't look like it allows me to change the icon once it's in the panel.

---

### Post by ComplexNumber on 2007-03-09
> **th3gh05t said:**
> Well, I figured this out!

You have to add the application to your Desktop first, change the icon, and then add it to your panel.

It doesn't look like it allows me to change the icon once it's in the panel.
another thing you can do is to change a line in the index.theme file(located in the icon theme) so that it 'inherits' from another OS X-type theme as well. that means, when the OS X theme doesn't have the required icon, it will look at that theme that it inherits and use icons from that theme instead. for example, my OS X theme inherits Aero, so i have the line:
Inherits=Aero.

---

