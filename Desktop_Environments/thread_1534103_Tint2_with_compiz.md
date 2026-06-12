---
title: "Tint2 with compiz"
date: 2010-07-19
forum: Desktop Environments
---

### Post by TheWeakSleep on 2010-07-19
I'm not entirely sure where to post this, so please move it if it's in the wrong section :)

I've been using tint2 as a panel/taskbar for the past few days, and I love it, besides one small issue. I'm using compiz for it's multiple workspace effects, and the taskbar on tint2 isn't detecting that there are multiple desktops, so when im on a different workspace, i can see the windows from the rest of them. I know that tint2 is supposed to be used with a window manager more like openbox, but I thought I might as well ask if theres a way to fix this :)

any ideas? thanks for the help :D

---

### Post by mcduck on 2010-07-19
That's something you can easily change in tint2's configuration file. You can set it to display windows from only the current workspace or all workspaces separated into groups (which pretty much allows you to use tint2's task bar as a desktop pager).

Just find the "taskbar_mode" -line in the setting file and change it from "multi_desktop" to "single_desktop".

---

### Post by TheWeakSleep on 2010-07-19
Thanks for the reply, though I've used both modes and they both have the same issue

---

### Post by lufte on 2010-09-20
It's kind of a bug. I have the same problem and as far as I know, there is no way to solve it unless you use a different window manager. It has something to do with with, in case you have four desktops, compiz using the option desktop_size=4 instead of using number_of_desktops=4. You can see both of these options in the compiz config settings manager. In my case, the number_of_desktops slider is grayed out and I guess this is your case too.

---

