---
title: "Ubuntu Battery meter color"
date: 2009-04-13
forum: Desktop Environments
---

### Post by Kniple on 2009-04-13
Hello dear people of ubuntuforums.org.

Im new here, but im not new to linux, one thing i was wondering, is it easy to change the colour of the current theme, (click appearance - colour) With some easy way each time my batterymeter changes colour? I.e. when low on battery, my theme goes to a dark orange colour, and green one when full. 

Is it possible to easy change the colour with a terminal command? From there i should be able to do it myself, but it would be nice if i dont have to reinvent the wheel. :)

Thank you!

---

### Post by antikristian on 2009-04-13
I think those are icons. So if i'm right you would probably have to change the icons manually.

But there are other iconsets in System -> Appearance (Theme -> customize -> icons)

Also, there are plenty of iconsets on sites like gnomelook.org that you can install

---

### Post by Kniple on 2009-04-13
Well yes thanks, already checked in on the iconsets, was wondering about the who theme you know? Like i can switch the color of all the windows, was wondering if that could be done autmoaticy?

---

### Post by antikristian on 2009-04-13
Totally misunderstood your question initially:-P

Well, that would be cool. 

If the color of the theme is possible to change in gconf i guess it would be possible. Gconf is made up of xml, so you could probably change it with a bash or perl script that periodically checked battery status in proc or sys.

fire up gconf-editor or grep the xml file(files) to see if there is anywhere you can change the colour.

---

