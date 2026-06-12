---
title: "Temporarily disable shortcuts on the desktop?"
date: 2010-12-14
forum: Desktop Environments
---

### Post by Another Quixote on 2010-12-14
I'm currently trying to learn how to get around Blender, but I keep running into the same problem.  Blender relies heavily on shortcuts and keystrokes to navigate it's GUI, but very often they clash with the shortcuts on my desktop.  The result is that the desktop shortcut wins, making Blender impossible to use effectively. 

Is there any way to disable the desktop shortcuts temporarily while using the software, and then setting them back when I'm done?


Thanks in advance,

-Q

---

### Post by mcduck on 2010-12-14
Are you using Compiz (the "visual effects")? If yes, you could try switching to Metacity when working with Blender. it has much less stuff, meaning much less keyboard shortcuts that could mess with Blender's shortcuts. Plus you'd probably get better performance from Blender as well..

One easy way to switch between the two is to hit Alt-F2 and run "metacity --replace" (to switch to Metacity) or "compiz --replace" (to switch to Compiz).

I don't think either one has any way to disable keyboard shortcuts, so if the ablve solution doesn't do the trick your only option would be to configure the shortcuts in a way that they don't conflict with Blender's shortcuts.

---

### Post by Another Quixote on 2010-12-15
Hi mcduck,

That's put me in the right direction.  I thought the GNOME shortcuts were clashing, but it was actually a few of the compiz key bindings.  A good fix for me then was to set two different settings profiles in compiz and just switch between them.

I haven't used Metacity before, but I'll give it a look.  I've never had problems with compiz dragging on system resources yet.  But then, I've not tried running 3D modeling, or video editing software on linux before now. 

Thanks a lot.

-Q

---

### Post by mcduck on 2010-12-15
Metacity is Gnome's default window manager, so if you've ever used Gnome with desktop effects diabled then you have used Metacity.. ;)

Switching between Compiz&Metacity using those commands is just a smoother way than doing it from the Appearance-dialog, since this way your Compiz settings won't get messed up.

The benefit of disabling Compiz with Blender comes form the fact that Compiz uses you graphics card to render all the stuff, while Blender also tries to use the GPU to draw it's whole user interface. Disabling Compiz leaves all the GPU power to Blender. So it will not affect rendering speed or anything like that, but depending on your graphics card&drivers it can make Blender's UI work much smoother.

---

### Post by Another Quixote on 2010-12-15
Ah OK.  Being new to linux, I have not heard Metacity explicitly named before.  Thanks for the added description, that helps a lot.

---

### Post by Another Quixote on 2010-12-15
Ok one other thing, when I switch to metacity using the "metacity --replace" command my desktop becomes really unresponsive, draws windows without title bars, chuggs and finally completely freezes.

This never happened from the fresh install, that is, before I started using compiz.  So now I am confused.

---

