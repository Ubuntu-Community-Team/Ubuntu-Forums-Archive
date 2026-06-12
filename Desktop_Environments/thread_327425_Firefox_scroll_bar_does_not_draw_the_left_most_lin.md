---
title: "Firefox scroll bar does not draw the left most line on Kubuntu 6.10"
date: 2006-12-29
forum: Desktop Environments
---

### Post by grybba on 2006-12-29
I've installed firefox package on a new installation of Kubuntu 6.10. The firefox works great except for a small annoying detail - while using the right scroll-bar to navigate on the page the left most line of the scrolling bar is not being redrawn as I move the bar with the mouse. The result is that the slider moves except a one-point leftmost line of it. 

I used some kind of Mozzilla patch available in the Desktop setting but it didn't change anything. Does anyone have an idea what to do about it?

Thanks.

---

### Post by glepore70 on 2007-01-02
I'm having the same problem, I think it has something to do with GTK Styles and Fonts in control panel, but the fix doesn't seem to do anything.

---

### Post by NeoChaosX on 2007-01-02
Yeah, it's a long-standing bug in the GTK-Qt theme. The "fix" only works for scrollbars within a page, not the main Firefox scrollbar. Probably the only way to fix it is to use a proper GTK theme (preferrably one that look similar to, if not exactly like, your KDE theme).

---

### Post by Jason Quinn on 2007-04-11
I'm not sure they are talking about the same problem as you are, NeoChaosX. The vertical line that they are referring to (at least for me) still exists even after installing the "scrollbar fix". They are talking about the 1-pixel wide left border of the scrollbar, not extra scrollbar buttons that the fix takes care of. Am I mistaken? Do you really mean the fix corrects the 1-pixel line for you? I'm trying to track down more info on this 1-pixel bug (to figure out if it is a Firefox bug or a gtk bug to help resolve an open buzilla ticket about it). Here is the that you are referring to:

[https://launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/47760](https://launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/47760)

Jason

---

### Post by ozar on 2007-06-21
A temporary fix for the scrollbar slider problem mentioned above is to add the following code to the *userContent.css* file in the** /.mozilla/chrome directory**:

```
scrollbar slider
{
        margin-left: -1px;
        border-left: 1px solid #8C8D90;
        margin-top: -1px;
        border-top: 1px solid #8C8D90;
}
```

---

