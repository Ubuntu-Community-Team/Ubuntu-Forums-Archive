---
title: "compiz fusion key binding problems"
date: 2007-09-05
forum: Desktop Effects &amp; Customization
---

### Post by |VeN| on 2007-09-05
so i finally took the plunge and put ubuntu on my desktop. Glad to say it was avery smooth process (even smoother than my laptop install :D)

So i wanted eye candy(compiz fusion) and decided to follow the how to on Forlongs Blog and it worked great and by default everything seems good. I decided to explore all this eye candy and personalize the binds. 

When i try to use the super key, or shift or alt or ctrl in the new bind (when it asks for the accelerator) it doesnt work! So i checked out the keyboard settings in ubuntu tried setting the win key as super and also meta and in both cases nothing happened. When i try to make a custom shortcut (say to open a terminal) using the super key all i can get in is Super L (shift ctrl and alt seem to work fine).

Has anyone else run into this issue or know of a fix? (i understand that im likely being a linux noob here but its puzzled me for the last hour!)

---

### Post by |VeN| on 2007-09-05
ignore this! as soon as i changed the window manager to emerald everything works!

---

### Post by Inxsible on 2007-09-07
> **|VeN| said:**
> ignore this! as soon as i changed the window manager to emerald everything works!
Please mark your thread solved, so others may benefit :)

---

### Post by MeanderingCode on 2007-10-16
having emerald as the window manager does not work for me.

Compiz and Emerald over XFCE.

I get a system beep (bell?)(Thinkpad T40p w/ Xubuntu Feisty) and no luck on setting keybinding.

Any ideas why?

Thanks.


EDIT:  If i double click on the action name to bring up the separate window, i can type the keybinding (i.e. <Alt>Tab), click ok, and that sets it.  I still get the above effect when i simply click the key column and attempt to pass the keybinding by "using" it.

---

### Post by khughitt on 2007-10-28
I found a bug relating to this issue on launchpad. I have not been able to get around this issue still. Anyone else have luck fixing?

The bug report is located at [https://bugs.launchpad.net/ubuntu/+bug/40866]("https://bugs.launchpad.net/ubuntu/+bug/40866") if you would like to share your experience.

---

### Post by MeanderingCode on 2007-10-28
Did you notice my edit? (Post #4, right before yours)

Double clicking on the action name brings up a window in which there's a text field you can edit to set the key binding.  Examples of syntax:
<Super>E
<Control><Alt>Left

pure keybindings:Key field
keys and clicks: button field

<Control><Alt>Button1 (for most of us, a.k.a. left click)

You get the idea.


NOTE: I consider this a WORKAROUND ONLY and the bug is still a bug (though i have no idea with what.

---

### Post by khughitt on 2007-10-30
> **MeanderingCode said:**
> Did you notice my edit? (Post #4, right before yours)

Double clicking on the action name brings up a window in which there's a text field you can edit to set the key binding.

I did see your edit above, however I didn't have any luck with that. Double-clicking the action name did not result in any window popping up for me. Are you using Gusty?

---

### Post by Sutur on 2007-10-30
Could it possibly be all the default keybinds that the plugins for compiz have defined?

---

### Post by MeanderingCode on 2007-10-30
> **pwnedd said:**
> I did see your edit above, however I didn't have any luck with that. Double-clicking the action name did not result in any window popping up for me. Are you using Gusty?

I am using Gutsy with Compiz from the repos.  It was the same for me using Compiz via Forlong's method.  i don't know what to tell you.  The only thing that comes to mind is a problem with window focusing and the popup opening behind your other windows, but otherwise i don't know.  Good luck.

---

### Post by khughitt on 2007-10-31
I got it to work using your method-- the problem was that I was trying to change the command in the gnome keyboard shortcuts manager. Double-clicking the name in the compiz manager (ccsm) allowed me to use the super key in combination with another key. The gnome keyboard shortcuts manager however still displays the (incorrect) binding used before.

Thanks :)

---

### Post by MeanderingCode on 2007-10-31
No problem.

> **pwnedd said:**
> The gnome keyboard shortcuts manager however still displays the (incorrect) binding used before.

It will. Someone correct me if i'm wrong, but it seems to me that window manager shortcuts are still honored, but overriden.  Meaning that if <Super>L is set to lock your session in the (i use XFCE) window manager's shortcuts, it will until you bind <Super>L to something in Compiz's shortcuts.

---

### Post by crazybilly on 2007-11-05
In what order do programs recieve keystrokes? I mean, the focused ap gets it first, then other user-started programs looking for global hotkeys, then the window manager, then the desktop, then the system itself or something like that?

(I totally pulled that order out of my butt as an example).

In any case, say I hit ctrl+shift+t, while running abiword in gnome with compiz as my window manager.  What programs are looking for that and in what order are they standing in line to recieve it?

---

### Post by MeanderingCode on 2007-11-05
> **crazybilly said:**
> In what order do programs recieve keystrokes? I mean, the focused ap gets it first, then other user-started programs looking for global hotkeys, then the window manager, then the desktop, then the system itself or something like that?

I'm not sure (i'd love it if someone who knew answered), but my experience says it's the reverse order you pulled out of your...errhm...

I think the "desktop" you're thinking of is the window manager, which generally manages the desktop.

> **crazybilly said:**
> In any case, say I hit ctrl+shift+t, while running abiword in gnome with compiz as my window manager.  What programs are looking for that and in what order are they standing in line to recieve it?

Based on my above said experience, system, window manager, global hotkey programs, focused window.

Any correction appreciated.

---

### Post by svivian on 2007-11-07
Thought I'd just add my experience to this thread. After I set up compiz, one of my shortcuts wasn't working (<Super>R set via gconf-editor > /apps/metacity/blobal_keybindings). At first nothing was happening but when I used it in an un-maximised window it zoomed in.

So I checked all the compiz prefs (System > Preferences > Appearance > Visual Effects > Preferences) and in the Actions tab of one of the plug-ins an action was set to <Super>R ! Changing the binding worked a treat!

---

### Post by crazybilly on 2007-11-08
that's pretty much what i tried, and it's still working for me.  <Super>e is slaying me, and I can't seem to get compiz to ignore it.

Grr.

---

### Post by MeanderingCode on 2007-11-08
> **crazybilly said:**
> that's pretty much what i tried, and it's still working for me.  <Super>e is slaying me, and I can't seem to get compiz to ignore it.

Just checking....in ccsm, the "module" is enabled (checked in general view or on left pane when viewing module itself)?  If yes and you want it so, can you clear the keybinding (click keybinding in action tab, changes to say "New Accelerator", hit backspace, now says Disabled)?

Just checking.

---

### Post by crazybilly on 2007-11-09
well, I checked it today and it seems to be working.  the hotkey, I mean.  

Maybe I had to reboot (once or twice)?  Maybe I needed to restart compiz or something? Shows what I know, huh?

Thanks for the help.

---

