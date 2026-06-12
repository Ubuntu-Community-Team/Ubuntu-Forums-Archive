---
title: "Conky resizing help"
date: 2009-05-05
forum: Desktop Environments
---

### Post by Delirium_Trigger on 2009-05-05
I attached a pic of my desktop and my Conky code to this post. 

How would I go about making Conky a bit thinner?
I copied most of that code from someone else, and I changed it a bit to suit my needs/use, but on my 15" laptop, it takes up a bit more room than I'd like.

Thanks!!

---

### Post by Delirium_Trigger on 2009-05-05
Bump

No answers?

---

### Post by gamblor01 on 2009-05-06
Line 13 -- you need to change the value of maximum_width.  Just lower it and play around with it until you find something that works for you.  Every time you change the .conkyrc file you will need to kill the current conky process and start it again though.  Very simple.


```

    background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    **[COLOR=Red]maximum_width 250[/COLOR]**

```

---

### Post by Delirium_Trigger on 2009-05-06
Thank you!
I didn't bother to look over the code; I would've noticed that if I had.

---

