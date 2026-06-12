---
title: "Can't drag&amp;drop windows from desktops on workspace switcher"
date: 2008-07-07
forum: Desktop Environments
---

### Post by adfe4sgsdg on 2008-07-07
Hi,
I have an ubuntu hardy with compiz running and I am no more able to move a window from a desktop to another dragging it on the workspace switcher applet. This is really annoying (I have to right-click on window top bar and send them using menus).
Anyone could help me solving this problem? I also tried to disable all the compiz options in Advanced Desktop Effects Settings that I have addittionally enabled after the installation but did not helped.
Ideas?
Thanks,
giorgio

---

### Post by sayakb on 2008-07-07
In Advanced Desktop Effects Settings, click on **Rotate Cube** and verify that **Edge flip move** is checked.

---

### Post by adfe4sgsdg on 2008-07-07
> **LinuxIsInnovation said:**
> In Advanced Desktop Effects Settings, click on **Rotate Cube** and verify that **Edge flip move** is checked.

mmmmhh even if I don't use the cube effect?

---

### Post by Ba66e77 on 2008-07-15
I don't use Rotate Cube either, but I enabled it just to see if it worked and nothing changed.  Until I installed the compizconfig-settings-manager
 package trying to figure out why I could no longer drag and drop windows from desktop to desktop, all I'd done with this visual effects stuff was to enable it in the Appearance Preferences.

Dragging items to other workspaces works fine with the visual effects off, but is there a way to make it pretty and functional at the same time? :)

---

### Post by sstvinc2 on 2008-07-27
I've got the same problem.  It doesn't even work for me if I disable the cube and go with Desktop Wall or Desktop Plane

Whenever I hover my mouse over something in the workspace switcher, the tool-tip that comes up says "Click to start dragging...", and when I then click and drag, the mouse changes to the correct drag-and-drop pointer.  But when I release the mouse, nothing happens.

This function does work in Desktop Expo for me, but I'd like to figure out a way to get it to work in the switcher as well.

---

### Post by gerbman on 2008-07-29
Same problem here. Try dragging a window from workspace 1 to workspace 4 using cube rotate...painfully tedious. The fact that the workspace switcher doesn't let you drag windows is enough to get me to turn off the effects altogether.

---

### Post by Potatoj316 on 2008-07-29
unless you go from workspace 1 directly to 4.  You arent going all the way around the cube are you?

---

### Post by gerbman on 2008-07-29
> **Potatoj316 said:**
> unless you go from workspace 1 directly to 4.  You arent going all the way around the cube are you?doh..bad example...1 to 3 is better, but it's beside the point anyway. simply not an efficient way to do it.

---

### Post by Potatoj316 on 2008-07-29
I usually use crtl+alt+shift+left/right to move windows around my cube.  There is also some key combination that moves the window without rotating the cube.  Kind of like a get this window out of my face command.

---

### Post by sstvinc2 on 2008-07-31
Thanks, but that's not really the problem.

I've done some more playing around, so I'll try to describe the problem in some more specific terms that might help us get some answers.  It seems like the workspace switcher isn't registering mouse movement after a mouseclick event.

Let's say, for instance, I'm on workspace 1 and I want to move a window from workspace 1 to workspace 2.  The resultant behavior is that nothing happens when I try to drop the window onto WS 2.  But, if I'm on WS 1 and try to move a window from WS 2 to WS 3, the resultant behavior is that my view gets switched over from WS 1 to WS 2.  In other words, it registered that I clicked on WS 2 but not my mouse movement, so when I relase the mouse, it still thinks that the pointer is over WS 2, so it takes me there.

I hope this wasn't too confusing.  Also that it helps someone figure this out.

---

### Post by caspar_wrede on 2008-10-19
Still present in intrepid and really rather annoying.

---

### Post by sarthorks on 2009-04-16
The problem is still there. I can't drag and drop windows in  the workspace switcher. 
In the configuration editor, if you go to DESKTOP > GNOME > APPLICATIONS > WINDOW_MANAGER, you will see this:

```

Key name : /desktop/gnome/applications/window_manager/number_of_workspaces
Key owner : gnome
Short description : The number of workspaces (deprecated)
Long description : The number of workspaces the window manager should use This key has been deprecated since GNOME 2.12.
```

And above, no_of_workspaces is designated <no value>. Even if you give it a value, it doesnt help.

Can anyone shed some light?

---

### Post by Somnus07 on 2009-06-16
um did anyone solve this problem? It is still in jaunty...

---

### Post by jlindbergh on 2009-10-11
Yeah, something ought to be done about this. That tool-tip confuses me too... A simple fix to remove it altogether would be okay, though fixing the real issue is preferred.
But, as I see it, removing the erroneous tool-tip would be the simplest (and perhaps ugliest) "fix".

---

### Post by beezdiego on 2009-10-31
I am new to Ubuntu and new to the forum.  

I have a curious and, I think, similar problem in Ubuntu 9.04.  Whenever I am set the Appearance-Visual Effects to "None" mode I can move application windows between workspaces in the switcher icon on the bottom of the screen, but I cannot move them by click-dragging them to the next workspace screen (left, right, up or down).  But the opposite is true when the Visual Effects are set to "Normal" mode.  I can click-drag windows between workspaces on the desktop but not in the switcher icons below.  

Is this a bug or was it intentional?  I figured it makes sense to turn off the click-drag feature in the Visual Effects "None" mode to save those of us with whimpy graphics cards, but why disable using the workspace switcher icon just because you can do it on the desktop.  I'd kind of like the option of doing it either way in "Normal" mode, but that is just not the way it works.

---

### Post by DistantDave on 2009-11-01
So at the moment is it a straight choice between either Compiz *or* the Workplace Switcher applet?

---

