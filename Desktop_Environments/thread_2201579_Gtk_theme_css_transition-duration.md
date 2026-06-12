---
title: "Gtk theme css transition-duration"
date: 2014-01-25
forum: Desktop Environments
---

### Post by Tristan_Williams on 2014-01-25
I have the Numix gtk theme installed and i am using it as my default theme in Xfce.

I went to /usr/share/themes/Numix/ and tried to figure out how to edit but i cant figure it out.

Basically heres what I want:

When I move or resize windows, I want them to have an opacity of 50%
That part is simple, however, I dont want it to just go instantly to 50% opacity,
I want it to have a transition-duration of 250ms. 

How can I do this, and where do I need to put it in the Numix configuration?


If I cant do it for just the windows during resize/move, could I apply it to everything like this?
```

* {

        transition-duration:                250ms;

}

```

---

### Post by Frogs Hair on 2014-01-25
As you may know in window manager tweaks - compositor you can set transparency of the windows during movement among and other things. Would it be fruitful to attempt to affect the change from the compositor rather than the theme  so it would be applicable to all themes ?  You might look into the application at the link. [http://www.webupd8.org/2013/06/xfce4-composite-editor-easily-change.html](http://www.webupd8.org/2013/06/xfce4-composite-editor-easily-change.html)

---

