---
title: "which process is responsible for slowing down the kubuntu?"
date: 2013-08-07
forum: Desktop Environments
---

### Post by DrAlbert on 2013-08-07
Hi.
My Kubuntu system during heavy disk activity is very slow. It does not seem logical because some activity like Mouse shaking or moving a window has nothing to do with hard activity (while the swap is not used).  so:

1 - Why activities not related to hard disk (like moving a window) are slowing down during hard disk activity?
2- which process is responsible for this slow down? for example kwin or plasma-desktop?
3- if kwin is responsible, is it possible to change the niceness of that process (kwin) during startup?

please help.

---

### Post by Jonathan Precise on 2013-08-08
> **DrAlbert said:**
> Hi.
My Kubuntu system during heavy disk activity is very slow. It does not seem logical because some activity like Mouse shaking or moving a window has nothing to do with hard activity (while the swap is not used).  so:

1 - Why activities not related to hard disk (like moving a window) are slowing down during hard disk activity?
2- which process is responsible for this slow down? for example kwin or plasma-desktop?
3- if kwin is responsible, is it possible to change the niceness of that process (kwin) during startup?

please help.

When you preform heavy disk activity, this uses up a lot of RAM (memory). Desktop effects (like moving windows) also use RAM. When the RAM gets low in space, then the computer becomes kind of sluggish. This is normal. However, if you want a system that's less "sluggish", try XFCE as a desktop environment or LXDE, as they have less Desktop effects:).

Xubuntu comes with XFCE by default, and Lubuntu comes with LXDE, so those are options.

---

### Post by SeijiSensei on 2013-08-08
Open a Konsole window and type "top" at the command prompt.  You'll see a report on memory and processor usage and a list of active processes.  If one of them is hogging the system, it should be at the top of the list.  Leave the window open as you use the computer and, if things slow down, see what top reports.

Did you create a swap partition when you installed?  If not, you should add a swapfile to your system by following the instructions here:  [http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

