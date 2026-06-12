---
title: "Can I remove an application from alt-tab?"
date: 2005-12-22
forum: Desktop Environments
---

### Post by reuben on 2005-12-22
Hello,

I use a combination of alt-tab & kompose for my task switching. I don't use the taskbar at all (in fact it isn't present.)

Anyway, is there a way to remove an application from the alt-tab list? I see that I can remove it from the pager & taskbar by editing advanced - special application settings (from the button on the top left of the window) ... however, I don't see anything for alt-tab in there. Is alt-tab built into kwin? Or is there some way to hack it?

Thanks

---

### Post by asimon on 2005-12-23
Does it work if you start the application via
```
kstart --skiptaskbar <application>
```
At least here it doesn't appear in the ALT-TAB windows list when started via kstart, I tested this with konsole. But if this works, then I  think it should work with the "special application settings" in kwin too. Maybe a bug?

And yes this "Walk Through Windows" feature is implemented in kwin.

EDIT: According to [KDE Bug 106818](http://bugs.kde.org/show_bug.cgi?id=106818), the "hide from pager&taskbar" setting in the advanved special application settings you mentioned, should hide it in the ALT-TAB too. It seems this functionality is not seperated currently.

BTW, there are several open bugs regarding this windows list, especially in interaction with some focus policies. I have read that a major rewrite is planed for this stuff in KDE 4.

---

### Post by reuben on 2005-12-23
Hm, actually removing from taskbar doesn't remove it from alt-tab for me. Maybe something is buggy with my setup. 

Thanks for the in theory info. Also, I voted for the bug you pointed out.

---

