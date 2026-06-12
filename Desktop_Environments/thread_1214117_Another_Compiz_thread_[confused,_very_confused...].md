---
title: "Another Compiz thread [confused, very confused...]"
date: 2009-07-15
forum: Desktop Environments
---

### Post by AVDa on 2009-07-15
So, it all began with the Gnome Desktop Environment...

Maybe two weeks ago, I formatted Vista off my laptop in favor of Ubuntu.  Everything has been great so far, however I'm having some issues with compiz.  

At first I had Gnome desktop env, and now I have Xfce for the sake of resources.  (it's a laptop and all)  It seems that the installation of compiz has wiped out the option to adjust the window decorations; i.e. the ability to change the minimize, maximize, shade, menu, and exit buttons on the window.  I imagine that there is a solution, but I'm still a super-newb on linux and need either help from the forum or a miracle to fimgure it out.

Also, when I installed compiz, it also wiped out another function.  I cannot access the "window manager" or "window manager tweaks" options.  The tweaks aren't completely necessary, however it would be nice to see it working again.

In the most basic sense, I only wanted a window switcher icon to show up so I didn't have to utilize a panel.  Unfortunately, it works off and on and I have to go back to my pager on the panel because the lack of that function seems to hide my homework.  

I've heard of blaming a dog for eating homework, but a penguin? 

Another issue that has come up is the keyboard settings.  It seems like Xfce's keyboard shortcuts memory is clashing with something else.  This one is really important because it helps with efficiency during studies.  Can you help with this one too?  I'll number the issues at the end of the post so they are more accessible.

If you can, explain in depth because it helps me learn when I think through it clearly.  

Thanks!  I appreciate the help in advance.

AVDa
(Aaron)
#short version of problems below.
-----------------------------------

1) Window Manager and Window Manager Tweaks disappeared in the Xfce settings menu

2) Is it possible to have a workspace switcher indicator without compiz, and additionally without an indicator in xfpanel?

3) My keyboard shortcuts are essentially wiped out and only work on occasion.  This has only come about when I started fumbling around with compiz and also the compiz-settings-manager.  Is there a separate program available, or the ability to edit keyboard shortcuts globally in a .conf file somewhere?

Thanks again!

---

### Post by AVDa on 2009-07-15
edit: I discovered part of the issue so far.  I'll keep you posted so I don't look too terribly stupid.

---

### Post by BinaryFeast on 2009-07-16
> 1) Window Manager and Window Manager Tweaks disappeared in the Xfce settings menuThese two items only apply to xfwm (the standard window manager for xfce). To tweak compiz you have to use the compiz fusion settings manager.

A tip would be to install fusion-icon, which will let you switch window manager on the fly.

About multiple desktops: I just use a keyboard shortcut (ctrl+alt+arrow) to switch between them, without any indicator.

---

### Post by AVDa on 2009-07-16
That sounds like a great idea.  I'd also like to learn about the .conf file if I can.  That way, I can see the inner workings and learn how the process takes place.  So, the first thing on the list is to remove the xfce version and return compiz-osd.

Considering the desktops:  I know how to shift between them, however my objective is to shift between them with an indicator so that I don't need the window switcher to display the present location.  Additionally, I bound keys, <alt>+<menu> to navigate between them without a window switcher.  In terms of longevity, the key bindings in settings editor > metacity > keybindings has worked the best.  Seeing that I'm the only one who will be working on my computer, I don't mind making permanent changes on it.  What would be *really* nice is the ability to have keybindings and notifications which are contextual to the program being operated.  Though, I imagine those types of settings are hard to come by.

The desktop switching icons may seem trivial to you, however they are important to me because 90+% of my time on the computer is for research purposes.  I need the ability to shift between work quickly and efficiently, including minimizing and maximizing windows and such.  In the end, I've found that while doing research at this level, seconds count and using a mouse is terribly inefficient.  A touch pad is even worse, btw.  

Simply put, within the context of compiz operation, I need:

1) A workspace switcher indicator, preferably that doesn't have a lot of extras included (animation, effects and others).  Low resources is key; it's a laptop and battery is important.

2) Notification indicators for things like screen brightness, sound control and some other specified programs: In other words, similar to what the Gnome desktop provides upon original installation.  

Thanks again for the help, and any additional words are very much appreciated.

-Aaron

---

