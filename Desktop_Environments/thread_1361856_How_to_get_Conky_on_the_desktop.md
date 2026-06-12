---
title: "How to get Conky on the desktop"
date: 2009-12-22
forum: Desktop Environments
---

### Post by harrisonk on 2009-12-22
[SIZE=4]Hello

I am trying to get conky to:

A. Start on login on the desktop.
and
B. Have a clear background.

Any ideas are appreciated.

Harrisonk

P.S For an example of what I want, it would be the same as Crunchbang#! Linux.
[/SIZE]

---

### Post by Wollombi on 2009-12-22
> A. Start on login on the desktop.

This can be done in a number of ways, but if you are using Compiz (or "Visual Effects" in Ubuntu), then there is usually a conflict on start up causing the Conky window to overshadow anything else.  So I use a script to make Conky start on a delay.  This gives me the added benefit of allowing my network connection to be established before Conky starts as well (I have some network dependent stuff).  I placed this script in my home folder and named it conky_start.sh

Here's the text of my script:
```

#!/bin/bash
sleep 10
conky &
/usr/bin/SpiderOak &
rainlendar2 &
exit 0

```

As you can see, I have a couple other items in there as well.  When the script is run, it will pause for 10 seconds, then start conky, then start spideroak, then start rainlendar2, and then exit.  To get the script to run on login:

1. Go to System > Preferences > Startup Applications.  
2. Click on the Startup Programs tab if you aren't already there
3. Click the Add button on the right.  
4. In the Name: field give it a recognizable name (i.e. Conky Start).
5. In the Command: field enter "sh /home/sean/conky_start.sh" without the quotation marks.  Be sure to change sean to the name of YOUR home folder.
6. Click Save
7. You should now see your new entry in the list of Additional Startup Programs.  Make sure the checkbox next to it is checked.  Then click Close at the bottom right.

On the next login, this script will run.


> B. Have a clear background.

For the clear background issue, make sure this is in the top portion (above the line that says TEXT) of your .conkyrc file:

```

own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

```

You don't *have* to use the last two lines, but I've found them to be helpful.  YMMV - you'll have to play with it and see what gives you the best results.

Good Luck!!

P.S.  Sorry if this is overly thorough/simplified - I'm just trying to make it as clear as possible and I don't know our comparative knowledge levels.

---

### Post by harrisonk on 2009-12-22
[SIZE=4]Thank you I will try that.

I am learning Python so go ahead and be technical.

Harrisonk
[/SIZE]

---

