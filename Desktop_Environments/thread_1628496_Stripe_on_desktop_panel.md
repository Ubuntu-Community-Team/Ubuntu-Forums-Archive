---
title: "Stripe on desktop panel"
date: 2010-11-22
forum: Desktop Environments
---

### Post by pauljam20 on 2010-11-22
Ubuntu 10.10 
There is a paler grey strip across the bottom of my panel at top of the desktop - this may be as designed, but I also get a paler stripe across the top of the Window when I run Audacity - this is obviously wrong.

Not terribly important, but when I look at things like this I always consider the impression it would make on a W______ user if I was trying to show them how good Linux was...

---

### Post by cbarron on 2010-11-22
It looks like it could be a GUI issue....either a graphics card driver issue or a gnome issue. I had problems with gnome for a bit untill I played with the graphics card driver (had to "roll" it back one). Im not the best linux person by far...it also looks like that grey strip has text in it and it also looks like it has a "reduce" box on the left. does this box show up only when you open a program? or is it there all the time?

---

### Post by koleoptero on 2010-11-23
The stripe on the panel is because the theme has a background for a 24 pixels wide panel, and you have it larger (or perhaps you have it at 24 pixels and the theme background is even smaller) so the panel tiles the image. You can fix that either by making your panel smaller (right-click on it, select properties, set the size to 24) or by using another theme / editing this one to not use a custom panel image (if you need help with that I can elaborate, just tell me which theme you're using).

About the empty space in the titlebar of audacious though I have no idea. It seems like a genuine bug.

---

### Post by pauljam20 on 2010-11-23
You are right that the panel is wide, it is 36 pixels. I think the problem is to do with the Ambience theme, I've changed to another one and it has gone.

I had a closer look at the Audacity problem, it is a horizontal slice of the very top of a list of input and output choices and I worked out that it is the device toolbar. I used the view/toolbars/device toolbar to remove and replace it somewhere sensible. I hadn't used Audacity since upgrading to 10.10, so it appeared as part of that upgrade. I've had odd problems with Audacity menus appearing in odd places before, but I'd forgotten because I haven't used it for a while.

All sorted, thanks for jogging my memory!

---

