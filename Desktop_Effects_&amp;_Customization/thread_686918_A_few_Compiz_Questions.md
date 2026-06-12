---
title: "A few Compiz Questions"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by intense.ego on 2008-02-03
I just migrated from Feisty to Gutsy and am still getting accustomed to Compiz-Fusion, and I have a few questions:

1) For the watter effects plugin, I accidentally set it to start when I type "a". when I try changing to change it to something else, it doesn't work and just shows me the "Actions" page like how it was. What do i do (I currently have it disabled so it doesn't start every few seconds when I am typing)?

2) On Beryl, I used to be able to drag the corner of a window and when i let go it would bounce back. here, when i do that, the window just "restores". I tried fiddling around with the settings but I could not find out how.

That's it for now.

---

### Post by aidanr on 2008-02-03
```
gedit ~/.config/compiz/compizconfig/Default.ini
```

Search for the section:
[B][water]
[/B]
And put in a different value for:
**as_initiate_key =**

The seach for the section:
[B][move]
[/B]
And change from true to false:
**as_snapoff_maximized = false**

---

### Post by intense.ego on 2008-02-03
The first step doesn't work for me. The termianl says the command wasn't found.

---

### Post by aidanr on 2008-02-03
It's not a command, that first line is the location of the compiz config file and the second is the section of the config file and the third is the option to change. I'll edit it to be more clear.

---

### Post by rainwalker on 2008-02-03
To stretch maximized windows like that, you can Alt + click near a corner and drag, or you can move your mouse to the very edge (like you would if you were going to resize it) and when the resize arrow appears click and drag it back.

---

### Post by intense.ego on 2008-02-04
> **aidanr said:**
> It's not a command, that first line is the location of the compiz config file and the second is the section of the config file and the third is the option to change. I'll edit it to be more clear.
The compand brings up a document with nothing in it.

> **rainwalker said:**
> To stretch maximized windows like that, you can Alt + click near a corner and drag, or you can move your mouse to the very edge (like you would if you were going to resize it) and when the resize arrow appears click and drag it back.

thank you very much!

---

### Post by aidanr on 2008-02-04
Well that's where the configuration file is for me, have a look at the hidden files in your home directory, see if you can find it. For the second question, I pressumed that when you said "restores" that the window restores to it's original size when you try bending it back, that sounded like the snapoff maximised windows setting to me but maybe I misunderstood.

---

### Post by intense.ego on 2008-02-04
I will have a look. Yes, I do believe that your advice was what i was looking for, but the advice from rainwalker does nearly the same trick. I only use that aspect of compiz to show off anyway.

---

### Post by ispy on 2008-02-04
i'm pretty sure you can change the value in CCSM, then log out and back in. wrked for me... I didn't need to open a terminal.

---

### Post by intense.ego on 2008-02-04
I don't quite understand. Could you please elaborate?

---

