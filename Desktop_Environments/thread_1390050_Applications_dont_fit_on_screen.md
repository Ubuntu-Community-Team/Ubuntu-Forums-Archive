---
title: "Applications dont fit on screen"
date: 2010-01-25
forum: Desktop Environments
---

### Post by elliotbeken on 2010-01-25
hi all, 

i have got a new laptop and i have installed ubuntu 9.10 on it, every thing works fine and could not be better and it is a 64-bit distro :P

there is one small problem i have came across. some applications dont fit on the screen like GIMP ()when saving work() and handbreak (i cant resize the window either)

my screen is 15.X" and i have a resolution of 1366 x 768 (16:9)

i have included a screen shot to make it easy to understand

is there anything i can do ??

---

### Post by earthpigg on 2010-01-25
not that i know of, unfortunately. i faced similar problems on my netbook and never ended up finding a solution.

im posting in this thread so that if someone out there does find/know a solution, ill be able to find this thread again. :D

you could always file a bug report or feature request with the handbrake folks.

---

### Post by mcduck on 2010-01-25
> **elliotbeken said:**
> hi all, 

i have got a new laptop and i have installed ubuntu 9.10 on it, every thing works fine and could not be better and it is a 64-bit distro :P

there is one small problem i have came across. some applications dont fit on the screen like GIMP ()when saving work() and handbreak (i cant resize the window either)

my screen is 15.X" and i have a resolution of 1366 x 768 (16:9)

i have included a screen shot to make it easy to understand

is there anything i can do ??

Are you absolutely sure that you are using the correct resolution? It's hard to say for sure since you have resized that screenshot, but it sure does look a lot less than 1366x768...

If it really is that resolution, then there's not much that can be done. Find a more compact theme and use smaller font size. Set toolbar style to icons only.

In the end if nothing helps, then you'll just have to use Alt+left mouse button to move the windows around so that yo can access the parts that don't fit into the screen.

(filing a bug report won't help since it's not a bug, just a simple fact that small resolution displays can't display that much stuff at once. Feature request might be appropriate, but I's suppose the program's developers are not really targetting small resolution dispalys and instead prefer making the user interface as good as possible for more common resolutions)

---

### Post by elliotbeken on 2010-01-28
i have found a small solution to this i have the window that is to big selected and click:

```
alt + f7
```

this allows me to move the window and do what i need to do..:D:D

---

### Post by mcduck on 2010-01-28
> **elliotbeken said:**
> i have found a small solution to this i have the window that is to big selected and click:

```
alt + f7
```

this allows me to move the window and do what i need to do..:D:D

You can also simply hold down the Alt key, tht allows you to move a window from any point inside the window instead of just the titlebar.

Alt+Left button = move
Alt+Right button = resize

---

### Post by Zorael on 2010-01-29
As mcduck mentioned, the easiest way is probably to Alt+drag the window upwards.

This is a pretty large issue for netbooks, and the applications (that makes us suffer from it) really just need that window to be redesigned. I've filed a bug for this a while ago as affecting Pidgin's settings window, and recently Konversation's, too. (Perhaps there should be a central Launchpad bug to which we could just assign all affected packages.)

KDE4 SC has some HID guidelines stating that any window should have a maximum height of something like 576 pixels - or be resizable down to that size. GNOME likely has something similar, but unassociated apps belonging to neither camp have no obligation toward this.

Chromium's settings window is also too tall, but the only button there is Close (no Accept/Cancel), so as settings are applied as soon as you change them, you can safely ESC out of it without haxmoving the window upward.

---

