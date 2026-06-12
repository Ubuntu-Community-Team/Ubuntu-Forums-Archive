---
title: "How to view open windows on workspace"
date: 2012-04-27
forum: Desktop Environments
---

### Post by midden on 2012-04-27
I am considering a return to Ubuntu with 12.04 (I have been using Xubuntu since 10.10); however, one really irritating feature of Unity is that I cannot see what windows are open on a given workspace (in XFCE and Gnome 2 you can see the window tabs listed at the top or bottom of the screen). I realize that once you are on a given workspace you can type "Super W" to spread all windows in the current workspace; however, if I have many workspaces and want to switch among them, what I really need is an ability to toggle among workspaces while keeping the "Super W" view activated.

For example, what I want to do is:
1) Type "Super W" on the current workspace to see what windows are present.
2) Toggle among workspaces using "Ctrl-Alt arrows" while still seeing the spread window view.
3) Upon finding the correct workspace, choose the desired window to activate.

Is there any way to get Unity to behave in this way? If not, is there a way to restore the window tabs to the task ribbon at the top of the screen?

Thanks for your help

---

### Post by jroa on 2012-04-27
My Unity works exactly as you describe and I am using 12.04.  If your's is not working this way, I think you might be in 2D mode instead of 3D mode.

Also, in Unity, to the left you will see the programs that are currently running.  The ones that are active have a small triangle pointing at them.  If more than one instance of a program is running, clicking on the icon will bring up a small icon of each.  It is a little bit different than classic Gnome, but it accomplishes the same  thing.

---

### Post by midden on 2012-04-27
Weird. I am pretty sure that I am using Unity-3D because when I type:

echo $DESKTOP_SESSION

I get "ubuntu" and not "ubuntu-2D". This is a fresh install, although I am using a home directory that has seen many iterations of X/Ubuntu -- could there be some setting file there that is an issue?

Any other ideas?

---

### Post by midden on 2012-04-27
I should have mentioned that I have installed the 64-bit version of Ubuntu.

---

### Post by midden on 2012-05-01
My problem with the window picker appears to be a known [bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933776").

---

### Post by markbl on 2012-05-01
midden, maybe consider trying gnome-shell? I think the "dynamic" desktop management there is better. All launcher, application browse or search, windows/expo view (same as meta-w in Unity), and desktop management in gnome-shell is overloaded in the single activities view mode which is activated by the meta key or the top left hotspot. It is beautiful in its simplicity and functionality.

For the function your want here, you can immediately see small views of each desktop and can expo view any by click or ctrl-alt-arrow, or double-click to immediately select.

Just "sudo apt-get install gnome-shell" and you will get the GNOME option on your login window. Won't affect Unity or anything else. Add the gnome3 ppa if you want a bit more gnome 3.4.

---

### Post by jsavga on 2012-05-01
> **midden said:**
> My problem with the window picker appears to be a known [bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933776").

Yep, it's a bug and an irritating one at that. Please make sure to follow that bug link and click on "Does this bug affect you?" and maybe we can get this fixed.

---

