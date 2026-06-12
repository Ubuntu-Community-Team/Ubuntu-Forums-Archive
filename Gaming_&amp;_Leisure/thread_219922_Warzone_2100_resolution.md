---
title: "Warzone 2100 resolution"
date: 2006-07-20
forum: Gaming &amp; Leisure
---

### Post by DeemanXu on 2006-07-20
Hi guys.

I was wondering if any of you good people knew how the holy hell to change the reolution in Warzone 2100. I've tried the 'README' for help, and the commands it gives don't seem to work all i get is this:

bash: warzone: command not found
.

Someone put me out of my damn misery, so that i can enjoy this original, and, still the best damn 3dRTS of all time.

Many thanks, Dee.
:mrgreen:

---

### Post by Lord Illidan on 2006-07-20
How do you launch the game itself?

Like this?

./warzone2100 ?

---

### Post by DeemanXu on 2006-07-20
I click the icon in the folder /home/deemanxu/warzone.2100.

---

### Post by Lord Illidan on 2006-07-20
> **DeemanXu said:**
> I click the icon in the folder /home/deemanxu/warzone.2100.


Then go in a terminal, Applications -> Accessories -> Terminal, and type these commands
```

cd warzone **[PRESS TAB HERE]**
 ./warzone -fullscreen -1280x960 **[REPLACE the numbers by X and Y resolution]**

```

---

### Post by DeemanXu on 2006-07-20
Thanks a lot m8, it worked like a dream, and hopefully that will help someone else out too.

Dee :mrgreen:

---

### Post by Perfect Storm on 2006-07-21
You can also open the config file in /.warzone-2.0 with a text editor to get all the options.

By the way if people want to compile warzone instead of using autopackage I wrote a howto here: [http://gaming.gwos.org/index.php?option=com_content&task=category&sectionid=4&id=13&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=category&sectionid=4&id=13&Itemid=63)

---

