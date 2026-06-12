---
title: "murrina ugly firefox"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by Chymera on 2007-10-07
ok, so i have some murrina themes over here which are quite appealing... but, if i use them, firefox starts looking stone-ageish (buttons with that chisel look, just like windows 3.1, and the likes...) is this normal? how do I get ff to look handsome while using a murrina theme?

---

### Post by FuturePilot on 2007-10-07
You might need to install the murrine Gtk engine
```
sudo apt-get install gtk2-engines-murrine
```
Then reapply your theme.

---

### Post by Chymera on 2007-10-08
I've already done that, obviously, or else my murrine theme wouldn't have looked nice even in gnome. Its just that firefox, as well as synaptic, and a few other applications seem to not get the murrine theme applied to them...:confused:

---

### Post by FuturePilot on 2007-10-08
Synaptic or anything run as root are not going to have the theme applied because it's installed locally. I'm not sure why Firefox is doing that. It's not running as root is it? I doubt it though.

---

### Post by Chymera on 2007-10-08
ok, so is there any way to apply the theme globally, just as the human theme is applied globally by default?

---

### Post by mindtrick on 2007-10-08
> **Chymera said:**
> ok, so is there any way to apply the theme globally, just as the human theme is applied globally by default?

[http://www.mattvanstone.com/2007/01/change_gtk_themes_and_icons_fo/](http://www.mattvanstone.com/2007/01/change_gtk_themes_and_icons_fo/)

---

### Post by Chymera on 2007-10-08
ok, 10x for the info.... i've solved the issue with synaptic and the rest of the administrative apps, however i still get the sampe problem with firefox, just looks damn ugly.... any of you use murrina and firefox?

---

### Post by Batuhan on 2007-10-08
Yes I've tried different engines and I'm using murrina now. I've never had an issue with firefox.

A screenshot maybe?

---

### Post by Chymera on 2007-10-09
[IMG]http://i21.tinypic.com/1zg5nk3.jpg[/IMG]

here it is, in the upper part you see how the theme looks in nautilus, in the lower part, in firefox.

As you can see the hover effect in ff is reminiscent of the old redmond style :P

---

### Post by Chymera on 2007-10-10
so, did anyone using murrina and ff ever get smth similar?

---

### Post by FuturePilot on 2007-10-10
Do you have a link for that theme? It could possibly be a bad theme or something?

---

### Post by aidanr on 2007-10-10
You might need gtk2-engines-pixbuf

---

### Post by Chymera on 2007-10-10
> **FuturePilot said:**
> Do you have a link for that theme? It could possibly be a bad theme or something?

every murrina theme i tried has this problem 

I have gtk2-engines-pixbuf installed :( any other suggestions?

---

### Post by VictorR on 2007-10-11
I use Widgets for Firefox
[http://http://ubuntuforums.org/showthread.php?t=369596]("http://http://ubuntuforums.org/showthread.php?t=369596")

Not sure if this is related to your problem, as they are intended to change the look of on-line forms, but you could try. I used Murrina for a while and didn't noticed any problems with FF.

---

### Post by VictorR on 2007-10-11
Check this out:
[http://www.mozilla.org/support/firefox/edit#css]("http://www.mozilla.org/support/firefox/edit#css")
this may help.

---

### Post by Chymera on 2007-10-11
well, if you would have looked carefully at the screenshot you would have noticed that my problem isnt related to the content, but to the ff frame. 

Any other suggestions? This happens for ff64, and ff32 and swiftweasel32 as well

---

### Post by Chymera on 2007-10-23
bump...

---

### Post by Rien91 on 2007-11-01
I've had the very same problem... I didn't use the default firefox theme, but if I do use that default theme everything just looks all right.

---

### Post by VictorR on 2007-11-01
Just tried once more - switched to Murrina based GTK2 theme and Firefox immediately changed its look (actually I use Swiftfox, but it's the same). Firefox is not a GTK application, so it mimics the look of its underlaying OS, probably not always successfully. I've found this link, where it is explained, and also what one can do:
[http://www.mozilla.org/unix/customizing.html#ui]("http://www.mozilla.org/unix/customizing.html#ui")

Maybe this will help.

---

