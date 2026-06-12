---
title: "Command for changing subpixel antialiasing from RGB to VRGB"
date: 2008-05-02
forum: Desktop Environments
---

### Post by tupfzom on 2008-05-02
Hi all,

I have a monitor that can be rotated.  I can very quickly rotate the screen settings using the Grandr applet, but I also need to change the subpixel antialiasing from RGB to VRGB or back which is not handled by the applet.  The only way I know to do that is clicking my way through the System menu.  But this is Linux, and I'm confident there is some console command that does it as well so I can prepare a script that does both rotation (with "xrandr -0 left") and adjust antialiasing.

I have been torturing Google for hours, but I couldn't find any hint.  Can someone help me with this?

Thomas W.

---

### Post by encompass on 2008-05-02
If I am not mistaken this is a gconf setting... if it is... then it is a file... find the file... save it somewhere... then make your change... now all we have to do is make a script to make the file exchange or try to embed it into your rotate.  The later would be tough.  But I think you could do it.
I can try to help you... but it will take a while.
I would also report this to launchpad.net/ubuntu and they can add that feature to the next version of ubuntu.  Great feature to add.

---

### Post by rupali_4 on 2008-05-02
You can do everything you want to do in a day on [www.baajaa.com](www.baajaa.com). You can look at job openings, find a date, rent an apartment, sell your bike and buy used items. And if you are interested in showbiz you can post your profile along with pics and your video as well. Also Balaji Telefilms is conducting auditions on [www.baajaa.com](www.baajaa.com) . All this and lots more on [www.baajaa.com](www.baajaa.com) !

One of the new features added on [www.baajaa.com](www.baajaa.com) is Yellow Pages. You can create a simple listing of your business for free. But what is really interesting is that you can Create Your Own Website (with your Logo, 5 pics, Company Profile, List of Products & Services, Video) and you get a Free Premium Yellow Page listing. For just Rs.3999/- !
 
Thanks,

---

### Post by tupfzom on 2008-05-02
Thanks for your reply, encopass!  It gave me the hint for solving the problem!

> **encompass said:**
> If I am not mistaken this is a gconf setting... if it is... then it is a file...

Yes it is!  It's here:  ~/.gconf/desktop/gnome/font_rendering/%gconf.xml.  The Gnome key is /desktop/gnome/font_rendering/rgba_order.

> **encompass said:**
> find the file... save it somewhere... then make your change... now all we have to do is make a script to make the file exchange or try to embed it into your rotate.

That's not necessary with the great tool I just found: gconftool-2!  By typing

```
gconftool-2 -s /desktop/gnome/font_rendering/rgba_order -t string "vrgb"

```

everything is done!

Thomas W.

P.S.: How can I mark this thread as solved?

---

### Post by tupfzom on 2008-05-02
I now have two nice icons on my gnome panel (a "normal" screen and an upright screen) with two tiny scripts behind them.  To turn the screen upright:

```

#!/bin/bash
  xrandr -o left
  gconftool-2 -s /desktop/gnome/font_rendering/rgba_order -t string "vrgb"
done

```

and to turn the screen to "normal" position:

```

#!/bin/bash
  xrandr -o normal
  gconftool-2 -s /desktop/gnome/font_rendering/rgba_order -t string "rgb"
done

```

If someone wants to use the icons, I attached them.  They could be more fancyful (with some arrows showing they are for rotation), but they look good enough.  (I slightly edited the icon I found at /usr/share/icons/hicolor/scalable/apps/gnome-display-properties.svg.)

---

### Post by encompass on 2008-05-02
Good job! and thanks for posting your scripts it will help others later.
And if you like... you can simply make at the beginning that your problem was solved see below, or something similar.  Just edit your first post. :D

---

