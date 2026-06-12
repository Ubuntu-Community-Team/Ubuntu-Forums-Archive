---
title: "hide panel during full screen game"
date: 2007-06-11
forum: Gaming &amp; Leisure
---

### Post by Xceptiona1 on 2007-06-11
I would like to use Beryl, but find that World of Warcraft loads up with the top and bottom Gnome Panels showing. If I disable Beryl, then the panels don't show up (the game looks full screen as it should). Is there a fix for this, so I can leave Beryl turned on? Thank you

---

### Post by Cappy on 2007-06-12
From:
[http://ubuntuforums.org/showthread.php?t=452467&highlight=Beryl](http://ubuntuforums.org/showthread.php?t=452467&highlight=Beryl)
and
[http://ubuntuforums.org/showthread.php?t=432082&highlight=Beryl](http://ubuntuforums.org/showthread.php?t=432082&highlight=Beryl)

Summary:
Change your WoW shortcut to this (or put it in a file and launch it):
```

killall beryl &&
wine ThisIsYourPreExistingLineToLaunchWoW &&
beryl &

```

There are lots of different ways to do it automatically, check those threads.

---

### Post by Xceptiona1 on 2007-06-12
With killall beryl, I assume that kills the process for beryl, then after the game stops you are relaunching it, now will I need to relaunch the beryl manager as well, or does that stay running. Also will I need to refresh the window manager after I restart beryl or should it be fine this way? 

One last question, how would I go about putting the whole code as one line in the app launcher, do you seperate the line with ; or somthing?

Thanks for the great info and help.

---

