---
title: "[SOLVED] Neverwinter Nights WIndowed?"
date: 2007-10-02
forum: Gaming &amp; Leisure
---

### Post by LauraSakura on 2007-10-02
I installed Neverwinter Nights on this laptop and got it working. It's terribly slow, but  I haven't done the tweaks to fix it yet (that and this laptop is a bit old). However, I'm running into a problem. I cannot find a setting to allow me to run the game windowed/non full screen. I Wouldn't mind running it full screen, however once I open the game I am unable to go to another window without fully exiting NWN. My keyboard shortcuts (such at Alt-Tab) are ignored while inside NWN so there is no way to get out without closing the game. (Well, I can press ctrl-alt-F1 to go to a new session, but thats not really what I want to have to do). Any ideas on how to make it run in a window, or to allow it to use alt-tab? (I'm not sure if all full screen programs disable the alt-tab, or if its only NWN). Thanks. I'm running Ubuntu 7.04.

---

### Post by FrozenFlame22 on 2007-10-02
1. Open up the file nwn.ini

2. Find the [Display Options] section.

3. Change the following entries:
FullScreen=0
AllowWindowedMode=1

If those entries do not exist, then just add them in.

---

### Post by KhaaL on 2007-10-03
excellent tip, now i can multitask while playing NWN :D Thanks!

---

