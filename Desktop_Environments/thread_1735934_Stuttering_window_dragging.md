---
title: "Stuttering window dragging"
date: 2011-04-21
forum: Desktop Environments
---

### Post by Adrastus on 2011-04-21
[SIZE=3][FONT=Arial]Hi all,

I'm fairly new to ubuntu and I've been messing around with customizing my desktop/UI over the past week or so and I must have messed something up.  After I got sick of how slow Wallpapoz was to change backgrounds between workspaces (I'm using GNOME) I turned on the Wallpaper plugin in Compiz and turned off the nautilus desktop.  That worked great for the backgrounds but now whenever I try to drag windows around the cursor shudders and shakes and the wondows won't move smoothly.  I eventually get them to where I want them to go but it's very annoying.

So far, I have re-enabled the nautilus desktop and reinstalled nautilus with synaptic, neither of which did anything.

Has anyone had this issue and/or fixed it?
[/FONT][/SIZE]

---

### Post by Copper Bezel on 2011-04-22
Like many Compiz issues, this could be a video card issue. (I'm actually surprised that the Compiz wallpaper plugin worked without tweaking on 10.10; I hadn't heard of it doing so for anyone.) 

Just to clarify, you did turn off the plugin, but there was no effect and window movement was still stuttery?

---

### Post by Adrastus on 2011-04-22
[SIZE=3][FONT=Arial]I've turned off the plugin and turned back on the nautilus desktop in the gconf-editor.  

And the plugin didn't work without tweaking, I had to turn off the show desktop option for nautilus.

As for a video card issue, I find that very unlikely as I'd been using my current configuration with no problems for over a month with no problems until now.

Thanks for getting back to me by the way.
[/FONT][/SIZE]

---

### Post by Copper Bezel on 2011-04-22
Oh, I didn't mean that there was a *problem* with your video card; I mean that certain Compiz plugins handle the graphics card differently, if I'm understanding what's being said in [_this_]("http://ubuntuforums.org/showpost.php?p=10702550&postcount=437") thread. For instance, some people get performance issues with the Blur plugin or it won't activate at all (as referred to in that post) where my puny netbook GPU has no problems with it.

As for "work without tweaking," I'm aware of the gconf keys; my experience with the wallpaper plugin was that it didn't work properly without *creating a custom login session* suited to its quirks. = ) Again, strange interactions of graphics cards and your particular Ubuntu and Compiz version.

All of that's irrelevant to the present problem, however, if the stuttering persists even on turning off the plugin. Have you restarted the machine or logged out and returned to Gnome since you deactivated it?

---

### Post by Adrastus on 2011-04-22
[SIZE=3][FONT=Arial]Restarted several times and logged in/out all over the place.  When logging in I do have to go into a virtual terminal before it displays correctly, or I did when the nautilus desktop was disabled.

If this helps, I'm using a desktop with a dedicated Nvidia card and I can post more hardware info if needed.

And the shaking.stuttering most often occurs when I'm moving a window up vertically and my cursor is in the center of the desktop.  The window seems to catch on an invisible snag and the cursor is actually the thing that shakes.
[/FONT][/SIZE]

---

### Post by Copper Bezel on 2011-04-22
> When logging in I do have to go into a virtual terminal before it displays correctly, or I did when the nautilus desktop was disabled.

Okay, yeah, that was the quirk I was referring to. = )

> And the shaking.stuttering most often occurs when I'm moving a window up vertically and my cursor is in the center of the desktop. The window seems to catch on an invisible snag and the cursor is actually the thing that shakes.

I don't know that I can add much to this, then. I find it very strange that this problem is persisting even though you've reverted your changes. Is there any chance that you made some other change in the process of setting up the wallpaper plugin, either to Compiz or in gconf?

---

### Post by Adrastus on 2011-04-22
[FONT=Arial][SIZE=3]Well...[/SIZE][/FONT][FONT=Arial][SIZE=3]I did try and build nautilus from source to apply the transparent background patch as explained here:
[/SIZE][/FONT][FONT=Arial][SIZE=3][http://forum.compiz.org/viewtopic.php?t=34249](http://forum.compiz.org/viewtopic.php?t=34249)
but I wasn't successful.

Do you think that reinstalling Compiz would do it?  Are there other dependencies I should reinstall?  This is kind of a bummer since it's not happening with any other desktop environments or window managers.  Maybe it's a metacity thing?  Is there a way to reinstall all packages and libraries for Metacity and Gnome?
[/SIZE][/FONT]

---

### Post by Copper Bezel on 2011-04-22
Well, you're not actually using Metacity - Compiz isn't just the compositor but also replaces the window manager. In fact, the problem will probably go away if you switch to Metacity,

```
metacity --replace
```

but then you'd lose all the advantages of using Compiz. We really shouldn't have to do anything drastic here, though; I really think there's a setting saved somewhere that's been changed and is causing the problem. (And reinstalling applications wouldn't solve that directly, anyway; unless you specify otherwise, removing a package doesn't remove its settings.)

Here's a thought, before we try anything crazy: create a new user account and see if the problem is present for that user. If it's not, it's definitely a setting somewhere that somehow got toggled by something you did. If the problem does persist, then it does have to do with the installed software itself.

---

### Post by Adrastus on 2011-04-22
[SIZE=3][FONT=Arial]Copper Bezel,

Thanks for the suggestions, oddly enough my computer crashed--wouldn't come back from suspended--and when I restarted from that everything was fine.  So I'm not entirely sure what it was, but it looks like it's gone for now.  Do you know of any way to back up my compiz settings so that I can restore them if something like this happens again?
[/FONT][/SIZE]

---

### Post by Copper Bezel on 2011-04-23
Yeah, in CCSM, click Preferences in the lower left, then under Profile, click Export.

Glad your problem seems to have gone away, even if it would have been more reassuring to find an actual solution. = )

---

