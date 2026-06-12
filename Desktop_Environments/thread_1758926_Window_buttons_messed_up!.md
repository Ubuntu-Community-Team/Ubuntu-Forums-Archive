---
title: "Window buttons messed up?!"
date: 2011-05-15
forum: Desktop Environments
---

### Post by jacqueshappy on 2011-05-15
One day a while ago, I noticed that for some random reason, the -, [], X (minimise, maximise and exit) buttons on applications that used the gnome windows buttons (as opposed to applications like Chromium that use their own) had got huge. I use a customised clear looks theme. I didn't really care that much until today, I noticed they'd randomly decided to shift to the left of the application window as opposed to where I normally have them on the right! This, I cannot stand by and let happen!
Help me?!

---

### Post by jacqueshappy on 2011-05-15
For some reason, randomly the buttons went back to the right of my windows..... Still huge though...
I'm not really bothered about this anymore so I'll mark it as solved but if anyone seeing this could answer it for future stumblers...

---

### Post by Krytarik on 2011-05-17
The button order is affected by a theme upon choosing it, if it includes settings for them. But you can either manually change the order by modifying the key "/apps/metacity/general/button_layout" in "gconf-editor" or follow my earlier post to have a handy little tool for it ;-):
[http://ubuntuforums.org/showthread.php?p=10115757#post10115757](http://ubuntuforums.org/showthread.php?p=10115757#post10115757)

As for the look of your buttons/titlebars/borders, you can choose a better fitting one via "Appearance -> Customize -> Window Border".

Greetings.

---

### Post by jacqueshappy on 2011-05-19
> **Krytarik said:**
> The button order is affected by a theme upon choosing it, if it includes settings for them. But you can either manually change the order by modifying the key "/apps/metacity/general/button_layout" in "gconf-editor" or follow my earlier post to have a handy little tool for it ;-):
[http://ubuntuforums.org/showthread.php?p=10115757#post10115757](http://ubuntuforums.org/showthread.php?p=10115757#post10115757)

As for the look of your buttons/titlebars/borders, you can choose a better fitting one via "Appearance -> Customize -> Window Border".

Greetings.

Pretty cool stuff!
Now how, in this configuration editor, would I make the buttons go back to the right of the windows instead of left?
Here is what they look like:

---

### Post by Krytarik on 2011-05-19
> **jacqueshappy said:**
> 
Now how, in this configuration editor, would I make the buttons go back to the right of the windows instead of left?

Depends on how you would like to arrange them, obviously.

To set them to the default right-sided order, set the key "button_layout" there to:
```
:minimize,maximize,close
```

---

### Post by jacqueshappy on 2011-05-20
Great thanks! 
Took me ages to realise it was significant that the semi colon was at the start instead of at the end.
 Thanks a lot

---

### Post by Krytarik on 2011-05-20
> **jacqueshappy said:**
> 
Took me ages to realise it was significant that the semi colon was at the start instead of at the end.
 
Yeah, that makes the biggest difference. :P
And it's a colon, not a semicolon.

You're welcome!

---

