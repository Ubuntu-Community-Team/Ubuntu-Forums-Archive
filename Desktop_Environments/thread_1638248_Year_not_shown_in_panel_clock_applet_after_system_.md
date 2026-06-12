---
title: "Year not shown in panel clock applet after system update"
date: 2010-12-05
forum: Desktop Environments
---

### Post by themaheshrs on 2010-12-05
I updated my Ubuntu Desktop systems (2x 10.10 and 1x 10.04) within the last 2 days. After the update, the "clock" applet in the panel has stopped showing the year! Here is how it appears now:

Is any one else seeing something/anything similar? Has anyone been able to fix this? Can you please guide me on how to fix this issue on my systems?

---

### Post by ajgreeny on 2010-12-05
I don't think I have ever seen the year in the clock applet, unless you click on the applet to show the whole calendar, where the year does show.

---

### Post by sisco311 on 2010-12-05
Welcome to the forums!

> **themaheshrs said:**
> 
Is any one else seeing something/anything similar? Has anyone been able to fix this? Can you please guide me on how to fix this issue on my systems?

Open a terminal (Applications -> Accessories -> Terminal) and run:
```
gconf-editor
```

On the left pane navigate to **apps -> panel -> applets -> clock_screen0 -> prefs**. On the right pane edit the value of the **format** key to **custom** and the value of **custom_format** to something like **%a, %b %d %Y, %I:%M %p**. For available format options, see:```
man strftime
```

---

### Post by ajgreeny on 2010-12-05
Ah well!  You live and learn.

Thanks for that sisco, it's good to know, even though I don't want it at the moment.

---

### Post by themaheshrs on 2010-12-06
> **sisco311 said:**
> Welcome to the forums!



Open a terminal (Applications -> Accessories -> Terminal) and run:
```
gconf-editor
```

On the left pane navigate to **apps -> panel -> applets -> clock_screen0 -> prefs**. On the right pane edit the value of the **format** key to **custom** and the value of **custom_format** to something like **%a, %b %d %Y, %I:%M %p**. For available format options, see:```
man strftime
```

@Sisco311, your solution worked.

But, is this a new bug that has been introduced in the recent updates. Because I am 99.999% certain that the year showed up earlier. In fact, the display format was pretty close to what you have specified.

Thanks @Sisco311 for your help.

---

