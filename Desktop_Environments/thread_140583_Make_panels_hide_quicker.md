---
title: "Make panels hide quicker"
date: 2006-03-06
forum: Desktop Environments
---

### Post by zugvogel on 2006-03-06
Hello. I can't figure out how to increase the speed of the hiding / appearing of the gnome panels. Can anyone tell me how this is done? Am I just missing something?

Many thanks.

---

### Post by ComplexNumber on 2006-03-06
go to gconf-editor(if you can't find it in the menu, go to command line and type in gconf-editor) and search for "top_panel". there you will see a switch to change the hide_delay. do the same for bottom_panel.


another useful tip is to find the auto_hide_size. when you have set the panel to auto hide, there is usually about 6 pixels still showing of the panel. change this value to 0 and the panel will (almost) completely hide from view when its auto hidden.

---

### Post by zugvogel on 2006-03-06
Thanks, that's great.

---

### Post by ComplexNumber on 2006-03-06
let me know how you get on.

---

### Post by zugvogel on 2006-03-06
Oh it works fine - it's so much better now. Incidently it was changing the "/apps/panel/toplevels/panel_0/" values that affected it, rather than top_panel - Probably because this is a new panel I added myself rather than the original top or bottom ones. And it's good to have it completely hidden from view; It makes a small but significant difference when you only have a small laptop screen!

Many thanks for your help.

---

### Post by ComplexNumber on 2006-03-06
glad to help as always :). incidently, i didn't find out about the bit about completely hiding the panel until i started to investigate the gconf editor a bit more closely about 4 months or so ago. there is quite a lot of things that the user can change about their environment by doing a search in gconf editor. a lot of people ask that question (about completely hiding the panel), but relatively few people seem to know about it.

---

### Post by zugvogel on 2006-03-06
Yes, that's true - I'd never even looked in this config editor before (having been 100% Ubuntu for almost a year) and there is a surprisingly large amount you can do there. Although, you'd imagine such basic options for the panels would be available under panel "properties", since such editing of the config like that would be beyond a lot of users, and a 500ms delay on showing the panel can get very annoying very quickly!

---

