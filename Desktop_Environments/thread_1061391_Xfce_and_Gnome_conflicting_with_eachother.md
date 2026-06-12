---
title: "Xfce and Gnome conflicting with eachother"
date: 2009-02-05
forum: Desktop Environments
---

### Post by Bryantos on 2009-02-05
This is an extremely weird problem.

First off, I'm using Ubuntu 8.04 and just recently today decided to switch to Xfce and give another environment a try. As soon as I start getting the hang of it I start installing themes.

Well, when I did an alt-F2 (xfrun4 is the command, I believe), and did a gksu nautilus, all hell broke lose. It switched to the defualt Ubuntu 8.04 background for root, the heron, and nautilus came up.

Now when I log in using Xfce, my Ubuntu background (non-root, but the user background I set using Gnome) shows up, the Xfce toolbars at the top and bottom show up, and when I right click, I don't get the Xfce menu, but instead get the "Create folder, New Document, etc." from when I right click in Ubuntu. Also, its using my hotkeys I set with Xfce and using xfrun4, and not Ubuntu's run prompt.

However, when I log in to my Gnome session, everything seems to be in order. Its using everything from Gnome and nothing from Xfce.

I would like to get Xfce back to its normal self so I can play with it some more, because I like it. I guess running a gnome file manager was the mistake, but I would like to fix it. :o

Thanks for any help. :)

---

### Post by spazz135 on 2009-02-05
Ya I tried that once And had the same problem. What i  did was change certian modules that were on the gnaome theme so when i started uf Xfce it would come up like it should sorry forgot what modules it was like a year ago. And i prefer gnome over all of theme of course edited.:p

---

### Post by jpeddicord on 2009-02-05
This thread or post has been moved from the Desktop Effects & Customization forum as the posted content is considered off-topic.

Desktop Effects & Customization is a forum for discussing:
[LIST]
[*]Compositing managers such as Compiz
[*]Themes (window themes, widget themes, backgrounds, etc)
[*]Appearance preferences
[/LIST]
Your post did not fit any of these categories, so it has been moved.

Common types of off-topic threads include:
[LIST]
[*]GNOME/KDE/XFCE help in general
[*]Hardware problems not directly related to compositing
[/LIST]

---

### Post by maybeway36 on 2009-02-06
The problem seems to be Nautilus starting up in Xfce when it isn't supposed to. I'm not sure how to fix it, though.

---

### Post by spazz135 on 2009-02-09
hey you might want to download the simple compiz manager simple-ccs i think is the command to get the software if not here is the link [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

Hopefully this works for you and if you could tell me how do i get the beans to come in :popcorn:

---

### Post by snowpine on 2009-02-09
If you are using Nautilus outside of Gnome, you need to launch it like this:

```
nautilus --no-desktop
```

(with 'gksu' at the beginning if you want to run it as root)

I highly recommend using Thunar instead of Nautilus in Xfce.

Now, the question is how do you fix the damage already done? I think it's as simple as this. When you log out of Xfce, you should be asked if you want to remember the current session. Say 'no.'

---

