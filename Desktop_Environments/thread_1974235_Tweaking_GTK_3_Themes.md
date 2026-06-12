---
title: "Tweaking GTK 3 Themes"
date: 2012-05-05
forum: Desktop Environments
---

### Post by wmalam on 2012-05-05
Problem: Many themes are broken in 64 bit 12.04. But they could be fixed easily if there was a quick way to tweak the elements of a theme. For instance the fg/bg colors of the desktop's applications menu. (Xubuntu 12.04, but I think the problem is in GTK 3)

Does anyone know where I can find an end-user tutorial on GTK 3 config files? The best would be oriented to someone like me who just wants to tweak one or two things that aren't working, but a themer's tutorial would do. All I can find so far is programmer documentation.

Of course, a nice GUI gadget would be even better, but if one of those exists it has escaped me.

Thanks in advance

-------------------------------

PS - Every theme which has a light background for the applications menu also has a light foreground, with the result that the text is unreadable. Many themes have the same problem in certain dialogs. This is in both XFCE and LXDE (of course) and I'll bet it shows up in Unity once you go away from the standard themes. Since it is unlikely that multiple themes have the same error, perhaps the problem is a bug in GTK 3 (a bad default? I couldn't find the hex of the colors I wanted to change) and the solution is to wait for the fix.

---

### Post by vasa1 on 2012-05-05
> **wmalam said:**
> Problem: Many themes are broken in 64 bit 12.04. But they could be fixed easily if there was a quick way to tweak the elements of a theme. For instance the fg/bg colors of the desktop's applications menu. (Xubuntu 12.04, but I think the problem is in GTK 3)
IMO, some are broken in 32-bit as well.
> **wmalam said:**
> Does anyone know where I can find an end-user tutorial on GTK 3 config files? The best would be oriented to someone like me who just wants to tweak one or two things that aren't working, but a themer's tutorial would do. All I can find so far is programmer documentation.
I've spent some time reading the documentation. It clearly isn't for someone who isn't into this as a profession or vocation.
> **wmalam said:**
> Of course, a nice GUI gadget would be even better, but if one of those exists it has escaped me.
...Until then, a DIY approach may be needed if it's important enough. Here are some of [my attempts]("http://ubuntuforums.org/showthread.php?t=1967261").

---

### Post by wmalam on 2012-05-06
First: Thanks to Vasa1. Your links helped me get started.

A couple more useful things: 

There ARE some gui tools. You'll find several in the software center by searching on "color:" 

 **Gnome Color Chooser** is *almost* ideal. It allows you to change  interface elements more-or-less by the names by which we end-users know  them, not the bank-shot names used by the GTK config files (in  which it appears everything is indirectly something else). 

Unfortunately, Gnome Color Chooser is a 2.x tool, and there are some  things that can't be changed, such as the colors used by the system  applications menu, which other applications such as Thunderbird also use  for their menus. But it may let you change what you need to change.    

There are also several tools that allow you to pick colors from the  screen or from a picture of the screen and just get the hex/rgb names  for them. This would be useful for hacking the configuration files: If  the colors you want to change are set explicitly you can find them and  change them.

**The gtk+ configuration files** can be in two places: 
/usr/share/themes - is where the themes used by everybody live. You  don't want to hack these (even if you're the only user, it's a constant  sudo hassle) 

/home/you/.themes (aka ~/.themes) will override the global themes - copy  the themes here for easier hacking.

**I'm looking for a way** to force a theme to reload in BASH (XFCE but preferably something that would work for all DEs). Anyone?

---

### Post by wmalam on 2012-05-14
Well, duh. The Compiz Fusion (panel) Icon will reload the desktop, and hence the theme, with a mouse click. (I may as well keep notes here, where they may be of use to somebody).

---

### Post by rai4shu2 on 2012-05-14
GTK 3 is a Gnome project, and (as I expected) has been plagued by confusing issues lately. If you look at their [Design/Contribute]("https://live.gnome.org/Design/Contribute") site, they say:

> Contributing to GNOME design requires that you enter into a conversation with existing design contributors.

That is to say, searching for answers isn't good enough for Gnome devs. They have to be personally involved before you are allowed access to that information.

But this just raises the question: Why not just make that information available? What are they hiding and why?

You go to their [Design]("https://live.gnome.org/Design") site, and it's just a confusing mess. Can someone explain where the GTK 3 design information is? Why is it such a pain just to create a theme?

---

### Post by vasa1 on 2012-05-14
I don't know about Xubuntu. I've added Xfce 4.10 to an existing install of 12.04. But the Xfce devs [haven't embraced GTK 3]("http://blog.xfce.org/") in 4.10.

---

### Post by wmalam on 2012-05-31
Thanks to the hint below, I've got a work-around. 

**Don't use the appearance (theme) selector that is launched by XFCE 4.8 's Settings Manager.** Use the GTK 2.0 Change Theme, instead, in combination with the window decor selector that is part of the "OX" Window manager that is launched by the Settings Manager. (This is assuming you are using the XFCE4 window manager)

Why? For a novice like me, there's a whole train wreck going on here, starting with vague language in the two separate selection lists (which are part of separate dialogs). The basic idea appears to be to have color themes selected by one list, and window decor by the other, except the color theme selector /also/ selects button and other gadget styles. Moreover, if parts of the window decor involve bitmaps, (the title area, say) that will, of course, ignore the over all color scheme selected by the scheme picker.

The "Appearance" (don't use) and "GTK 2.0 Theme" (use) dialogues *mostly* select color schemes but also the appearance of certain interface elements other than the window frames aka "window decor." 

Even when this works as it should it is confusing and unfortunately designed. The two list boxes should be part of the same dialog, one labeled "Color scheme and gadgets" the other labeled "Window frames and decor." (Maybe this would be too hard to do with so many different window managers)

That's not the big problem, though. The big problem is that GTK have changed their configuration files in such a way as to break old configurations.

This means that applications compiled with one version of GTK might not be compatible with themes designed under a different version. 

It appears to me that GTK is mainly responsible for this problem because they have violated good practice by breaking the configuration interface. 

> **vasa1 said:**
> I don't know about Xubuntu. I've added Xfce 4.10 to an existing install of 12.04. But the Xfce devs [haven't embraced GTK 3]("http://blog.xfce.org/") in 4.10.

---

### Post by wmalam on 2012-06-11
The best solution, for those who are not content with brown and black, might be KDE. It's gorgeous out of the box and you can configure everything. 

I should emphasize that **the following is guesswork** on my part, based on what I think I observed while trying to fix what should have been a minor problem.

The combination of Unity's philosophy of controlling your desktop for you and changes in the theming interface between GTK2 and GTK3 such that backward compatibility was not maintained resulted in problems I couldn't easily fix for myself because Unity wouldn't let me. Unlike KDE, Unity has no way to easily tweak the elements of a theme, and I just wanted to change one thing, but couldn't without digging deep into GTK's configuration files. 

If I am not mistaken, KDE is still using GTK 2.x (?) The main visual disadvantage is that font smoothing is not as good as it is in Unity. (Later) Yes, it is. This laptop looks better if smoothing hints are set to minimum. 

XFCE had similar problems and I suspect Gnome will, also. XFCE relies on Gnome tools for some of the interface tweaking, and those tools haven't been updated for GTK 3 and are, for the most part, broken. This is the main reason I think GTK 3 breaks interfaces.

---

### Post by vasa1 on 2012-06-11
> **wmalam said:**
> Thanks to the hint below, I've got a work-around. 
...
I missed this post altogether. I'll have to bookmark this thread.

---

### Post by amgamgamg3 on 2012-07-03
If I got your meaning, you can open gnome-software-center and search:  "Ark" and download it, then open this software and open compressed theme  file and drag and drop compressed files from Ark to your desktop, then  make "tar" file of them by Ark, after that write in terminal: <cd  ~/Desktop> and enter and again type (FILE ==> your file name):  <gzip FILE.tar>
finished!
Ali.M (live in Iran)

---

### Post by amgamgamg3 on 2012-07-04
did it help you? or did I get your mean true?

---

### Post by amgamgamg3 on 2012-07-07
did it help you? or did I get your mean true

---

