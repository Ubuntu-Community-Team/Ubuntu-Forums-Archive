---
title: "change the ubuntu logo"
date: 2007-03-05
forum: Desktop Environments
---

### Post by drko on 2007-03-05
I am trying to make gnome look like mac osx as much as possible, and I trouble with change the icon in the top left corner from the ubuntu logo to the apple logo. I replaced the disrtibutor-logo in /usr/share/icons/hicolor/48x48/apps/distributor-logo.png with the apple logo but it still won't change. I am using edgy eft. Any help is appreciated

---

### Post by invalid on 2007-03-05
Assuming this is the correct file to replace, have you tried logging out and back in?

---

### Post by drko on 2007-03-05
> **invalid said:**
> Assuming this is the correct file to replace, have you tried logging out and back in?

yep, but if that isn't the right icon to replace, where would the right icon be?

---

### Post by drko on 2007-03-05
also, I would like to know if it is possible to change the possitioning of the close, maximize, and minimize buttons to the top-left corner instead of the top-right corner

---

### Post by ComplexNumber on 2007-03-05
> **drko said:**
> I am trying to make gnome look like mac osx as much as possible, and I trouble with change the icon in the top left corner from the ubuntu logo to the apple logo. I replaced the disrtibutor-logo in /usr/share/icons/hicolor/48x48/apps/distributor-logo.png with the apple logo but it still won't change. I am using edgy eft. Any help is appreciated
if the theme that you're using has a start-here icon, change that. don't change the distributor icon because, in most cases, it won't have any effect (its merely a link to start-here icon, in most cases). 
if the theme that you're using doesn't have a start-here icon, change the one in gnome (if not, try Human theme).

---

### Post by BLTicklemonster on 2007-03-05
You know, I have been thinking about this for a while. It would be nice if someone had a How To post like "pimp my ubuntu" where they showed you where to go to change everything from the initial ubuntu logo you see when you're booting, all the way through to what we see here. I think it would make for a pleasant experience for people to have the knowledge at their fingertips to totally whack out and customize their ubuntu. I wish I knew more, I'd post it myself!

---

### Post by jackusage on 2008-05-21
You'll have to check under the folder for whichever theme you're using. So, for example, go to /home/Yourusername/.icons/scalable/places/ , backup the start-here.png icon, and then replace it with whatever .png you want, renaming it start-here.png. Run:

killall gnome-panel

..in terminal and it should show up! Credit goes to Alex S. for finding this out.

---

