---
title: "Howto remove the entry that will stay in the Ubuntu Software Center?"
date: 2014-04-09
forum: Desktop Environments
---

### Post by helpkit on 2014-04-09
Hello,

I recently installed Gambas 3 and later I uninstalled it again with the Ubuntu Software Center. Now there will stay an entry in the menu's of the Ubuntu Software Center. However Gambas 3 insn't installed anymore. Also according the Ubuntu Software Center. How can I remove this entry? It just gets in the way of the eyes. I'm already looking for a while to remove this entry. Any help will be greatly appreciated. I also Googled.

[IMG]http://oi57.tinypic.com/jfalog.jpg[/IMG]

Thanks in advance for any help!

helpkit

---

### Post by grumblebum2 on 2014-04-09
You must have added a gambas ppa.The menu shows enabled software sources.
In the software centre go to 
menu > edit > software sources > other software
and unmark the gambas ppa.
There should be a **source** ppa for gambas as well. Unmark that also.
Close software sources and leave USC open while the cache updates.
You will see a progress meter while this is happening. May take a minute or so.
[ATTACH=CONFIG]251880[/ATTACH]

When the cache update has finished, close USC and then reopen.
I had to actually close and open USC a couple of times before a disabled ppa entry disappeared from the menu.


**PS**... If you want to take a screenshot of a menu dropdown use a delay with gnome-screenshot.
```
gnome-screenshot -d 5
```
or

to bring up a gui with interactive options use (typing screenshot in the dash does the same)
```
gnome-screenshot -i
```

I install **shutter** for screenshots which includes an editor for annotating the screenshot image,

---

### Post by helpkit on 2014-04-15
I unmarked gambas ppa already before. I made reboots to the system. Later I did again a reboot later and it was gone automatically.

Thanks anyway!


helpkit

---

