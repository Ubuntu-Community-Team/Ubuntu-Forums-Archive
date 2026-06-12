---
title: "SCIM Setup confusing. Any docs?"
date: 2009-06-16
forum: General Help
---

### Post by jcoles on 2009-06-16
I used SCIM for Chinese a couple of years ago, but I can't get it to do anything in Gnome on Ubuntu 8.10. 

The SCIM Input Method Setup application is baffling! So many potential settings for the English/Chinese switch. Which is the right one? 

If I look on the FrontEnd > Global Setup page, "Trigger" is Alt+slash. Doesn't work.

If I look in IMEngine > Smart Pinyin, the "Mode Switch" is "Alt+Shift_L+KeyRelease, Alt+Shift_R+KeyRelease, Shift+Shift_L+KeyRelease, Shift+Shift_R+KeyRelease". What is that?! Do I press all of these keys at the same time, or in a sequence? And what key is "KeyRelease"? Incomprehensible!

There's also a "Chinese mode switch" on that page, set to "Control+slash". Doesn't work.

When I used SCIM before, I remember doing Ctrl-Space or something like that and then seeing pop-up menus when I typed Pinyin. How do I get that again? 

In the Package Manager, I can only find API developer documentation. Where's the user documentation?

---

### Post by jcoles on 2009-06-17
I found a good guide to SCIM setup at [https://help.ubuntu.com/community/SCIM#Using]("https://help.ubuntu.com/community/SCIM#Using"). 

It helped me to install the right packages and tweak some configuration files. 

Now I just click the SCIM icon on my toolbar to select the language.

---

