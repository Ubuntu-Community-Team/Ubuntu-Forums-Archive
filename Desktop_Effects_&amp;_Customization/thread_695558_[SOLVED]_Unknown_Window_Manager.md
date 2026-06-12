---
title: "[SOLVED] Unknown Window Manager"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by Xoanan on 2008-02-13
HI All

I am still having some issues with Xubuntu after installing Compiz and Compiz Switch(useful tool)

I find that I use the pc more freely without CCM so, I don't use it, However, I would like the old window manager back. Here's what I am getting 


[ATTACH]59571[/ATTACH]

Any thoughts?:popcorn:

---

### Post by kpkeerthi on 2008-02-13
1. Make sure you Remove/Disable Compiz from Autostarted applications
2. Reboot (or kill compiz and restart 'X)
3. You will most likely not have window borders
4. Open a terminal or press ALT + F2 and type **xfwm4** and press <enter>

You'll be all set. XFCE's default window manager should automatically work next time you reboot.

---

### Post by Xoanan on 2008-02-13
Thanx!  I will try that and post back when I get a chance!

---

### Post by Xoanan on 2008-02-13
> **kpkeerthi said:**
> 1. Make sure you Remove/Disable Compiz from Autostarted applications
2. Reboot (or kill compiz and restart 'X)
3. You will most likely not have window borders
4. Open a terminal or press ALT + F2 and type **xfwm4** and press <enter>

You'll be all set. XFCE's default window manager should automatically work next time you reboot.

That did the trick!  Thanx!  I'll have to remember that one.:popcorn:

---

