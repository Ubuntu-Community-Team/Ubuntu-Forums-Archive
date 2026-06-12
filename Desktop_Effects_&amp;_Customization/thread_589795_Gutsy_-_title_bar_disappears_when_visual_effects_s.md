---
title: "Gutsy - title bar disappears when visual effects set to normal or above"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by kdfox on 2007-10-24
Linux virgin (first real install) using gutsy.  updated nvidia driver (the regular one not the new or legacy version).  when i enable visual effects i lose the title bar and all its associated functionality.  installed emerald (which was suggested in another thread but that only seemed to make things worse.  what to do?

---

### Post by Perpetual on 2007-10-24
Install compizconfig-settings-manager

```
sudo apt-get install compizconfig-settings-manager
```

Once installed, go to System>Preferences>Advanced Desktop Settings and make sure 'Window Borders' is enabled.

I'm not on Ubuntu at the moment, XP at work so some of my wording may be incorrect.  It will get you in the right direction though.

---

### Post by kdfox on 2007-10-24
did what you said but in the compiz config i don't see where i can enable window borders, but i'll keep looking.  thanks for pointing me in that direction. post if you remember any more specifics. Thanks!

---

### Post by Perpetual on 2007-10-24
It's actually the option for 'Window Decorations'.  Enable it and your borders ought appear.

---

### Post by kdfox on 2007-10-24
i enabled it and still nothing.  should i remove emerald?  reinstall my nvidia driver?

---

### Post by Perpetual on 2007-10-24
Just curious, did you restart x (ctrl+alt+backspace)?

---

### Post by kdfox on 2007-10-24
i hadn't.  tried it, but when it came back visual effects kinda snapped to "none", when i rest them it went back to (mis-)behaving as it had before.

edit:
when i changed the setting for "place windows" to disable, the visual effects reverted completely to the "none" setting, which explains the snapping in and out of effect i described earlier.

---

### Post by kdfox on 2007-10-24
i gotta get back to work, thanks for your help.  while the problem is not solved at least i  feel like i can navigate the system a little better.  if you get any more ideas, please post them here and i will check back on this thread later.  thanks again!

---

### Post by SaiGoN DraGoN on 2007-10-25
Ha ha!   i have been going in circles trying to get my title bar back; i kept doing emerald --replace, compiz --replace and nothing; and the problem was that i did not select windows decorations on compiz manager. Ha ha ha!
well the simplest answer is always the best.
Thanks!

---

### Post by Clarke on 2007-11-20
Selecting Windows decorations made no difference. I have the Nvidia card and only one thing that helped me to enable window titles is 
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by Akoi Meexx on 2008-03-18
I hate to necro an old old post, but I've noticed that if you disable the workarounds in compiz manager, it restores the titlebar and window borders. I had this same problem and I think it's incredibly ridiculous that it happens at all.

Alternatively, if that doesn't solve the problem, disable EVERYTHING in compiz manager except windows decorations. Then go through and systematically apply each item to see if it causes the error, and you have your problem. Hope this helps!

---

### Post by Schreck425 on 2008-04-07
Tried all of those,  still nothing for me.  Nvidia quadro 550.  Title bar disappears when I put the visual effects to normal or higher.  The funny thing is that it worked at first,  until I restarted the computer.  Then when it came back I had no title bars and haven't got them back since.

---

### Post by Akoi Meexx on 2008-04-07
If you updated any kernel headers, try reinstalling the nvidia drivers via Envy.

---

