---
title: "unity workspace switching"
date: 2017-06-22
forum: Desktop Environments
---

### Post by Skaperen on 2017-06-22
i set up workspaces and i got a new button.  left-clicking causes all the workspace to appear in a smaller form.  then i can click on which workspace i want to work on.  there is one problem i have run into with this which is that when i click on the workspace to work on, i sometimes am still moving the mouse and that ends up moving a window in that workspace.  is there a way to prevent that? or, better yet, is there a way to set up a button for each workspace to jump directly from any workspace, to the workspace for that button?

i already know i can right-click on the workspace button and get a little menu of the workspaces, but this is awkward to use.

i currently have 108 workspaces.  this is done by having 12 logged in user and a 3x3 workspace grid on each user.

my dream has for a long time to have such a desktop switch done by pressing Ctrl+Alt+some other key (or a few other combinations) to switch to a desktop unique for each key (combination).  the scheme i dream of would present a login screen the first time going to each desktop (so different userids can be used) and support a scriptable API to do autologins and switches, and logouts.  i'm not sure, yet, how i would implement such a thing, but VNC regularly comes to mind when i think about it.

---

### Post by mc4man on 2017-06-24
> i sometimes am still moving the mouse and that ends up moving a window in that workspace. is there a way to prevent that?
Stop holding down the l. mouse button, i.e. grabbing a window. As described you couldn't move a window to another window.

(- unless you've  somehow set up 'hover' means grab.
> is there a way to set up a button for each workspace to jump directly from any workspace,
Not in the expo plugin but certainly in the Viewport Switcher plugin.

---

### Post by Skaperen on 2017-06-25
> **mc4man said:**
> Stop holding down the l. mouse button, i.e. grabbing a window. As described you couldn't move a window to another window.

(- unless you've  somehow set up 'hover' means grab.
so you mean i should use the right mouse button (the center button has no action)?

> **mc4man said:**
> Not in the expo plugin but certainly in the Viewport Switcher plugin.
or a keyboard press, like Win+(keypad digit).  since i have a 3x3 grid of workspaces the keypad would make sense.

---

