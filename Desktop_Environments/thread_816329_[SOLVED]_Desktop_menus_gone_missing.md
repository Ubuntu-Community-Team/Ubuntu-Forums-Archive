---
title: "[SOLVED] Desktop menus gone missing"
date: 2008-06-02
forum: Desktop Environments
---

### Post by belfasttim on 2008-06-02
Hi-- I upgraded to 8.04 a week or so ago on a Toshiba laptop. The upgrade went smoothly and all seemed well. I booted this morning to discover that all the menus and desktop bars (top and bottom) have disappeared. I have reinstalled compiz (following another post) with no luck.

Any ideas on this? It seems there's a lot of posts with similar issues but not really any answers.

thanks

---

### Post by kshane on 2008-06-02
> **belfasttim said:**
> Hi-- I upgraded to 8.04 a week or so ago on a Toshiba laptop. The upgrade went smoothly and all seemed well. I booted this morning to discover that all the menus and desktop bars (top and bottom) have disappeared. I have reinstalled compiz (following another post) with no luck.

Any ideas on this? It seems there's a lot of posts with similar issues but not really any answers.

thanks

***I THINK*** you can use "gnome-panel --replace" in terminal to get the panel up again...

Kevin

---

### Post by belfasttim on 2008-06-02
> **kshane said:**
> ***I THINK*** you can use "gnome-panel --replace" in terminal to get the panel up again...

Kevin

Thanks Kevin. I tried this command and got a "command not found" error.

Is it possible that gnome-panel got blown away or something?

---

### Post by kshane on 2008-06-02
> **belfasttim said:**
> Thanks Kevin. I tried this command and got a "command not found" error.

Is it possible that gnome-panel got blown away or something?

I suppose so.  Try "apt-get install gnome-panel"

Kevin

---

### Post by belfasttim on 2008-06-02
Kevin, you helped me put my finger on it. Turns out I tried to get rid of evolution in favor of Thunderbird (it's my dad's machine and he doesn't use it for anything but email and web) and it tossed out gnome-panel as well.

Thanks for the help!

---

### Post by Het Irv on 2008-06-02
Yeah, Evolution is tied to so much stuff in Gnome that if you remove Evolution, Gnome will crash.  I wish that that would change, but untill then I am just going to hide it.

---

### Post by kshane on 2008-06-02
> **belfasttim said:**
> Kevin, you helped me put my finger on it. Turns out I tried to get rid of evolution in favor of Thunderbird (it's my dad's machine and he doesn't use it for anything but email and web) and it tossed out gnome-panel as well.

Thanks for the help!

No prob!  Glad you got it figured out.  I can relate!  I have never (beyond when I initially installed Ubuntu) tried to use evolution as Thunderbird works very well and covers all my email needs.  Also, since I like and use firefox, it just makes sense to me to use it...

Good luck!

Kevin

---

