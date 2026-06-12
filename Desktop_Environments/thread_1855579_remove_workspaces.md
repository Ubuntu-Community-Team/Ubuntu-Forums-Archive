---
title: "remove workspaces"
date: 2011-10-06
forum: Desktop Environments
---

### Post by th00ht on 2011-10-06
Ubuntu 11.4 came with 4 workspaces and workspace swithcer installed. I need only one workspace. how do i disable workspaces and remove workspace switcher?

---

### Post by Copper Bezel on 2011-10-06
Do you have compizconfig-settings-manager installed? If not, install it from the Software Center and open it. Then select the General Options plugin and, from there, the Desktop Size tab. Reduce the horizontal and vertical size to 1.

You don't need to disable the workspace switcher if you only have one workspace, but it's another Compiz plugin that you can turn off. Note, though, that if you're using the Unity interface, you can't remove the button from the dock/Launcher.

If you're new from Windows, though, try the workspaces out for a bit. They can be very useful for keeping yourself organized if you're handling several tasks at once.

---

### Post by collisionystm on 2011-10-06
> **th00ht said:**
> Ubuntu 11.4 came with 4 workspaces and workspace swithcer installed. I need only one workspace. how do i disable workspaces and remove workspace switcher?

You can always boot into Ubuntu Classic and edit the Workspaces on the gnome panel. Just right click it and go to properties. Changer workspaces to 1

---

### Post by Krytarik on 2011-10-06
> **Copper Bezel said:**
> You don't need to disable the workspace switcher if you only have one workspace, but it's another Compiz plugin that you can turn off. Note, though, that if you're using the Unity interface, you can't remove the button from the dock/Launcher.
This [thread]("http://ubuntuforums.org/showthread.php?p=10762054#post10762054") indicates that Unity's Workspace Switcher will be automatically gone if you set at least "Horizontal Virtual Size" to "1".

Extending *Copper Bezel*'s reference to the plugins; if you reduce your workspaces to a single one, you could _theoretically_ disable "Expo", "Desktop Wall", and "Viewport Switcher". But as the  both first mentioned ones are dependencies of the "Ubuntu  Unity Plugin", disabling those would disable the latter, and thus kill your desktop, if you are using Unity! Compiz doesn't take into account that you have only one single workspace enabled, and that running the mentioned plugins, therefore, makes no sense.

But +1 for trying out the workspaces feature!

Regards.

---

### Post by cyiucsy on 2011-10-06
I have been using Ubuntu for like 4 years and one of the things that I love so much is the workspace design!

For example, when you are doing something about projectA and then suddenly you got a phone call and you need to read and look for some information about projectB, then **_if you keep all the windows opened in one single workspace, it's easy to mess up things_**. However, you can switch to workspace-2 where it's clean without anything about projectA and finish your projectB there and then switch back to workspace-1 to continue with your projectA.

And I always switch to a new workspace if I want to take a break, like play some small games/surf the net. :popcorn: And then I will switch back to continue working.

I had to use MS-Windows sometimes and I actually installed a freeware called "Dexpot" to get a similar functionality. Just can't live without it.

So, I agree with all of the above comments and I suggest you to give it another try. :p

---

### Post by th00ht on 2011-10-09
Thanks ciucsy

Is this the Simple CompizConfig Settings Manager?

I have used multiple desktops on solaris, smaltalk, windows, mac and quite seriously with todays screen sizes they're bit of a waste. :-) 

It is interesting that ubuntu comes with more and more applications (without asking) and leaves out these settings

---

### Post by th00ht on 2011-10-09
Thanks collisionsystm

There is no workspaces on the gnome-panel. The Simple CompizConfig Settings Manager cannot be installed. (something about a missing dependence)
So I guess there is no longer a simple way to remove multiple desktops and I will have to live with this.

Thanks all for your help.

---

### Post by Copper Bezel on 2011-10-09
No, *not* "simple ccsm." The package is compizconfig-settings-manager.

---

### Post by th00ht on 2011-10-12
> **th00ht said:**
> Thanks collisionsystm

There is no workspaces on the gnome-panel. The Simple CompizConfig Settings Manager cannot be installed. (something about a missing dependence)
So I guess there is no longer a simple way to remove multiple desktops and I will have to live with this.

Thanks all for your help.

Oh, I got it. It is at the bottom right side. Right click on it and change the settings

Got rid of all the superfluous screens on my multimedia center.

Like I said: thanks all!

---

