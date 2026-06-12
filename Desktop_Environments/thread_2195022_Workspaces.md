---
title: "Workspaces"
date: 2013-12-21
forum: Desktop Environments
---

### Post by durward2 on 2013-12-21
I am using Ubuntu 12.04 upgraded from Ubuntu 10.04. The Workspace indicator is gone from the bottom of the screen. On my Ubuntu 13.04 - Gnome machine, the workspace  indicator is at the top.

How do I  change workspaces? How do I get the indicator back on the desktop?

My SystemSettings -> Details show ubuntu12.04LTS, Memory 1.7GiB with AMD Phenom 9600 Quad-Core Processor;VESA:RS780 grapics,32 bit. 

I think I installed Gnome 3.

Also, how do I get the day of the week and date to show with the time in the center of the top bar?

---

### Post by deadflowr on 2013-12-21
Workspace is now an icon on Ubuntu.
Look at the launcher at the left.
It looks like a window pane.

If you want the clock in the middle of the panel
try installing gnome shell.
```
sudo apt-get install gnome-shell
```
which is like Ubuntu's shell but not.
when install log out of the session and before logging back in, click the icon next to you username in the log in screen and choose Gnome.
Have fun.

---

### Post by grahammechanical on 2013-12-22
Most of the icons in the Laucher are moveable. We can drag them and put them back in the Launcher at a higher or lower position. You may have done that with 13.04 and forgotten that you moved the Workplace switcher icon from the bottom to the top. In versions of Ubuntu Later than 12.04 the Workplace switcher icon is not on the Launcher by default. We have to go to System Settings>Appearance>Behaviour and tick a box to Enable Workspaces.

Please remember, that 12.04 is radically different from 10.04. And Ubuntu 13.10 also has differences from 12.04 as considerable improvements have been in the meantime. Furthermore, Ubuntu Gnome is not meant to be looking backward to Gnome 2 panel. But to show what Ubuntu would look like if the developers had not only accepted Gnome 3 desktop environment but also Gnome 3 Shell instead of using Unity.

In Ubuntu 13.10 we can install from the Software Centre Gnome Session Flashback. That will give us 2 extra options at login; Gnome Flashback (with Compiz) and Gnome Flashback (with Metacity).

In Ubuntu Gnome 13.10 we can install a Gnome Shell extension called Gnome Classic. Flashback and Classic have different code bases. That are not to be thought of as the same. They give a similar look to that of 10.04 but they do not fully replicate Gnome 2 and Gnome 2 panel.

I have found, from experiments, that Gnome Session Flashback does not work well on Ubuntu Gnome 13.10. And I see no reason for installing Gnome Classic on Ubuntu-Unity 13.10 when we have Gnome Session Flashback.

Regards.

---

### Post by durward2 on 2013-12-23
On my 12.04 LTS, when I go to System Settings > Appearance, the only choices I have are Background, Wallpapers, and Theme. There is no Behaviour.

---

### Post by deadflowr on 2013-12-23
> **durward2 said:**
> On my 12.04 LTS, when I go to System Settings > Appearance, the only choices I have are Background, Wallpapers, and Theme. There is no Behaviour.

There are two tabs on top.
Look, and Behavior.

Though, you didn't state if you have the launcher resize option(which is under the themes dropdown option)
I think this might be part of the unity-2d session.

But enabling the workspaces is not needed in 12.04. They already are enabled.
It would be the releases after 12.04 that need to have the workspaces enabled.

Look at the bottom of the launcher at the icon above the trash icon.
That is, if you haven't mounted any extra drives.
The launcher for precise would be from the bottom on to the top, trash, then any mounted devices, then the workspace switcher icon.
Then any added launchers and the top most is the dash.
This holds true for both unity and unity-2d.
(except I don't where what the mounted devices show in unity-2d, I think it's the same)

---

