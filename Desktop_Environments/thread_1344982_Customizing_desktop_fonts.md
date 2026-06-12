---
title: "Customizing desktop fonts"
date: 2009-12-03
forum: Desktop Environments
---

### Post by sideburns on 2009-12-03
My sister is running the latest Ubunutu, and has just changed her wallpaper.  Now, the labels on her icons don't show up as well as they used to, so she needs to change their color.  Alas neither of us can find where that's done any more.  (I use Fedora, also with Gnome, and can't find it on my box either.)  I'd appreciate a pointer to wherever it is we need to go to get this corrected.  Thanx in advance for any help.

---

### Post by blackened on 2009-12-03
> **sideburns said:**
> My sister is running the latest Ubunutu, and has just changed her wallpaper.  Now, the labels on her icons don't show up as well as they used to, so she needs to change their color.  Alas neither of us can find where that's done any more.  (I use Fedora, also with Gnome, and can't find it on my box either.)  I'd appreciate a pointer to wherever it is we need to go to get this corrected.  Thanx in advance for any help.

The search box is your friend, this has been answered many times before.

Open gedit with an empty file, then paste the following text into it:
```
style "desktop-icon" {
     NautilusIconContainer::frame_text = 1
      text[NORMAL] = "#FFFFFF"
     NautilusIconContainer::normal_alpha = 44
}
#class "GtkWidget" style "desktop-icon"
widget_class "*DesktopIcon*" style "desktop-icon"
```

Change the hex code value of the normal text entry to the color you want.

Save that file as ~/.gtkrc-2.0 then log out and back in (or kill and restart nautilus) to see the effect.

---

### Post by sideburns on 2009-12-03
> **blackened said:**
> 
Change the hex code value of the normal text entry to the color you want..

Neither my sister nor I have any graphics experience and have no idea what hex code means what color.  For us, and probably about 90% of all Linux users, this information is utterly useless.  In Winderz, you can select the color for the icon labels from a table; why can't you in Gnome?

---

### Post by Raffles10 on 2009-12-03
You can install gnome-color-chooser, makes life a lot easier. :D

```
sudo apt-get install gnome-color-chooser
```

---

### Post by wojox on 2009-12-03
That's really good info.

Hex colors: #FFFFFF = White  #000000 = Black

[Hex Colors]("http://www.december.com/html/spec/color.html")

---

### Post by sideburns on 2009-12-03
OK.  As it turns out, I already have that on my Fedora box and was able to test it.  I'll pass it on to my sister, ASAP.  Thanx!

---

### Post by blackened on 2009-12-04
> **sideburns said:**
> ...have no idea what hex code means what color.  For us, and probably about 90% of all Linux users, this information is utterly useless...

I was, of course, trying to help you accomplish what you wanted in a way that I know to work. Sorry if you took it as off-putting.

And your assumption that 90% of Linux users have no idea what hex code is would, I think, prove patently false if put to a proper (and very unscientific) forum poll.

> **Raffles10 said:**
> You can install gnome-color-chooser, makes life a lot easier. :D

```
sudo apt-get install gnome-color-chooser
```

Heh, nice catch. Never seen that one before, oddly enough.

---

### Post by sideburns on 2009-12-04
> 
And your assumption that 90% of Linux users have no idea what hex code is would, I think, prove patently false if put to a proper (and very unscientific) forum poll.


Try not to take things out of context next time.  I said that 90% of all Linux users wouldn't know which hex code belonged to which color, not that they wouldn't know what a hex code is.

---

### Post by blackened on 2009-12-04
> **sideburns said:**
> Try not to take things out of context next time.  I said that 90% of all Linux users wouldn't know which hex code belonged to which color, not that they wouldn't know what a hex code is.

I didn't take it out of context, but simply misread it. Right you are about few people knowing which hex codes belong to which color. In fact I would put it closer to 100%. I've been using them for years and could probably give you 5 to 10, and most of those would be shades of gray. And from back in my days of dealing with crappy binary transparency in Windows there's the lovely magenta (#FF00FF).

I really didn't mean anything malign by my comments, quite the contrary really. Guess I just come off as gruff in print. Maybe I lack proper emoticons. :D

Glad you got it sorted though, now that we're fully off-topic.

---

