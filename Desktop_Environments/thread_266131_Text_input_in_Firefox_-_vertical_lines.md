---
title: "Text input in Firefox - vertical lines"
date: 2006-09-26
forum: Desktop Environments
---

### Post by anroy on 2006-09-26
I am running the Dapper Drake 6.06 version.

I find that when I enter text in any input box displayed in Firefox (including the input box I am typing into at this very moment :)  ) I get these ugly vertical line artifacts between the characters if I move the caret backward with the Back arrow key.

A picture is worth a thousand words.
[[IMG]http://img137.imageshack.us/img137/6045/textlinespx0.th.jpg[/IMG]](http://img137.imageshack.us/my.php?image=textlinespx0.jpg)

Interestingly, when I try to take a screenshot these lines disappear, as if it is trying to hide the evidence.  :lol:   So I had to take that photo of my monitor with a digital camera.

It has been this way since I first installed this OS, a couple of months back. I should have mentioned this earlier but have suffered in silence the whole time.

Does anyone have this issue?

---

### Post by anroy on 2006-10-17
bump :)

---

### Post by garrgh on 2006-12-10
The vertical lines are ghosted versions of your caret and this is covered [elsewhere in the forums]("http://ubuntuforums.org/showthread.php?t=91017").  I originally searched for "vertical lines" as well, so figured it would be helpful to not leave this thread unresolved.

I found I had to install the proper Nvidia drivers.  [This tutorial]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") was the most helpful with that.  It provided step by step instructions and didn't assume any knowledge about editing xorg.conf, for instance.

---

### Post by anroy on 2006-12-12
> **garrgh said:**
> The vertical lines are ghosted versions of your caret and this is covered [elsewhere in the forums]("http://ubuntuforums.org/showthread.php?t=91017").  I originally searched for "vertical lines" as well, so figured it would be helpful to not leave this thread unresolved.

I found I had to install the proper Nvidia drivers.  [This tutorial]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") was the most helpful with that.  It provided step by step instructions and didn't assume any knowledge about editing xorg.conf, for instance.

Thanks a lot for pointing me to the right thread and to the nVidia site.  

It wouldn't have occurred to me to call them sticky carets although that is indeed accurate.  :)

---

