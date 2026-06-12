---
title: "Unity: Workspace Management customization?"
date: 2011-06-02
forum: Desktop Environments
---

### Post by arpad9 on 2011-06-02
My apologies for posting this twice - the first time I had a poorly chosen title.

First hour with Unity. First impression: Ewww.

It seems like Unity is designed more for the average newbie than for the power user. Yet, I'm willing to give it a shot.

Can anyone help with the following things I'm missing now (that I had in Compiz)?

1. I had Ctrl-Alt-<workspace number> setup to move the current window directly to that workspace. (Ctrl-Shift-Alt-Arrow?? Really? Four keys at once and a couple of arrow pushes???)

2. I had Ctrl-Shift-<workspace number> to move the current window directly to that workspace without following it.

3. Pressing the middle button on the desktop initiated grabbing the cube and turning it.

4. Moving the scroll wheel while on the desktop would rotate the cube.

Thanks for any hints for getting some functionality back. Workspace management is one of the greatest things in Compiz. Without that, I might as well get a Mac or some other less advanced GUI.

---

### Post by Bonster on 2011-06-03
open up "Keyboard Shortcuts" to change your keys and install ccsm to do cube and button binding

> sudo apt-get install compizconfig-settings-manager

---

### Post by arpad9 on 2011-06-03
What you're suggesting is that I also re-enable desktop cube... which will disable the Unity plugin (not sure what that will do).

I was really more interested in trying to figure out what this Unity UI will do.  It's amazing to me that it seems so limited.

---

### Post by 3Miro on 2011-06-03
You can enable both Unity and the Cube at the same time, but it is tricky.

By default, Unity uses "Desktop Wall", which allows for the same key-binding customizations as the Cube (move to workspace, move window to workspace, go left/right/up/down ...)

There are additional shortcuts under "Viewport Switcher", which can also be safely activated.

---

### Post by arpad9 on 2011-06-03
Thank you, I appreciate that.  However, is there no hope for the customization and the spirited, productive use of Unity?

---

### Post by 3Miro on 2011-06-03
> **arpad9 said:**
> 
1. I had Ctrl-Alt-<workspace number> setup to move the current window directly to that workspace. (Ctrl-Shift-Alt-Arrow?? Really? Four keys at once and a couple of arrow pushes???)

2. I had Ctrl-Shift-<workspace number> to move the current window directly to that workspace without following it.

3. Pressing the middle button on the desktop initiated grabbing the cube and turning it.

4. Moving the scroll wheel while on the desktop would rotate the cube.


Unity is a plugin for compiz. If you are running Unity, then you are running compiz. Most plugins for compiz work with Unity (except the cube that requires extra work).

Install CCSM and adjust compiz the way you want it, just as you would on 10.10. CCSM also provides some Unity specific customizations, such as the size of the icons.

1 and 2 are adjustable from CCSM Desktop Wall plugin

for 3 you get the wall not the cube

4 can be set via the Viewport Switcher plugin

---

