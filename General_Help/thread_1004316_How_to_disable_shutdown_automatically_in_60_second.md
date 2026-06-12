---
title: "How to disable shutdown automatically in 60 seconds?"
date: 2008-12-07
forum: General Help
---

### Post by joehte on 2008-12-07
Hi,

since I installed Ubuntu Intrepid, the shutdown dialog has a very annoying feature of doing shutdown automatically in 60 seconds if nothing is selected.

Now don't laugh, but I have a 1.5 year old boy who often presses my computer's power on/off button which triggers displaying of that dialog. It often happens I don't notice it and my machine shuts down as the automatic shutdown in 60 seconds is done. There was no automatic shutdown in Hardy Heron, and when he pressed the button I could just close the dialog when I noticed it.

So please... it's driving me insane. Is there anything I can do to disable this new (mis)feature?

---

### Post by mk1w86 on 2008-12-07
Although this is for Xubuntu it should also apply to Ubuntu. :D

[http://ph.ubuntuforums.com/showthread.php?t=873892](http://ph.ubuntuforums.com/showthread.php?t=873892)

---

### Post by meson2439 on 2008-12-07
... or you could just remove the power button from the panel. You could shutdown using the terminal by typing:

```
shutdown -P now
```

and if you want to restart:

```
shutdown -r now
```

you can replace now with hh:mm (24 hour format).

---

### Post by mk1w86 on 2008-12-07
> ... or you could just remove the power button from the panel. You could shutdown using the terminal by typing:

Code:

shutdown -P now

and if you want to restart:

Code:

shutdown -r now

you can replace now with hh:mm (24 hour format). 


I think he means the power button on the computer itself.

---

### Post by meson2439 on 2008-12-07
Yup... you're right. He could just disable the power button. But if it was me, I would have remove the whole panel. Alt-F2 is good enough for me to run everything.

Kids love to click. So I would remove everything worth clicking. He will get bored as long as he observe nothing interesting. :p

---

### Post by joehte on 2008-12-09
> **mk1w86 said:**
> Although this is for Xubuntu it should also apply to Ubuntu. :D

[http://ph.ubuntuforums.com/showthread.php?t=873892](http://ph.ubuntuforums.com/showthread.php?t=873892)

Thanks,

this works great!

Removing the power button entirely from the computer would be problematic since then I'd have a hard time putting the computer back on ;).

---

### Post by Poodle Doodle on 2010-03-22
Re: Shutdown, Logout, Restart ... 60 sec time

Me thinks the 60 second off cycle is too long.


Me thinks OFF means OFF and not "In a little while".



As in 44 magnum hand gun into Toyota Prius engine block, via the dash board and CPU.

"When I say stop, I mean stop"..... "Booyah, Booyah, Booyah, Booyah"

Toyota Prius stops.


Same thing with computer.

Me thinks 5 seconds for reconsideration tops.

Anyone have THE answer to this?

---

