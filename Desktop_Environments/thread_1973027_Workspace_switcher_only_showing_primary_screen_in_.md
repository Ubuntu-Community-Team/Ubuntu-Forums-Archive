---
title: "Workspace switcher only showing primary screen in Gnome-shell"
date: 2012-05-04
forum: Desktop Environments
---

### Post by michaelmestre on 2012-05-04
I have tweaked Gnome-shell (3.4) to have workspaces extend over both screens in my dual-monitor setup.
Everything is working fine, except that the workspace switcher/pager only shows the windows on the primary screen.

This is a bit confusing because I have to browse all the workspaces to find the windows that are on the secondary screen.

Does any solution exist to this problem ?

---

### Post by PirateFanAZ on 2012-05-04
I have the same issue.  I would suggest you try to install dconf-editor using the Software Center.  Run it from a command like (sudo dconf-editor) and navigate to org/gnome/shell/overrides.  You'll see a setting there related to multiple desktops switching, it should be the last setting listed.  It will be checked to provide the behavior you are seeing.  Uncheck it, close dconf-editor and see what switching desktops looks like.  You may need to log out of Gnome and log back in.

I tried this on my Ubuntu 12.04 (upgraded from 11.10) but it didn't seem to work.  I do think this is the correct way to change this behavior though.

---

### Post by michaelmestre on 2012-05-04
No, checking the option you are mentioning will /disable/ workspace switching on the secondary monitor.
I don't want to change this behavior: I only want the pager to /display/ the windows that are on the secondary monitor (for each workspace).

Best regards,
M

---

### Post by mojo2012 on 2012-06-28
I need this feature too. But this seems not to be possible at all ... :-(

Not even through an extension or plugin ...

---

### Post by draptik on 2012-07-02
The previously described solution by PirateFanAZ works:

Open dconf-editor > org > gnome > shell > overrides

Uncheck the box labeled "workspace-only-on-primary"

I did not even have to restart Gnome, it worked right away.

At least it works with an out-of-the-box Arch Linux with current Gnome installed... Your milage might vary with current Ubuntu.

---

### Post by markbl on 2012-07-02
> **draptik said:**
> The previously described solution by PirateFanAZ works:

Yes, but as the OP says above that is not the problem he is describing here. Also, changing that dconf setting is cumbersome and old advice anyhow. Recently that setting was added as a simple toggle button in gnome-tweak tool which is more or less the "official" place to set gnome-shell options.

---

### Post by mojo2012 on 2012-07-09
Doesn't even one of the gnome shell dev team use more than one screen?

It's really shocking how such basic bug has never been fixed ... :-(

---

### Post by lolpenguin on 2012-07-12
The workspace selection is for the primary monitor only. :(

---

### Post by markbl on 2012-07-12
> **lolpenguin said:**
> The workspace selection is for the primary monitor only. :(
That's just the default option. If you want it on all monitors then change it by just pressing the button in gnome-tweak-tool/Shell.

---

### Post by mojo2012 on 2012-07-12
It's interesting, but all over the internet people ask the same question and always get the same wrong answer ... :-\

@markbl: di you read the previous posts? michael and me already have this option enabled. Switching itself is NOT the problem - IT WORKS!

The problem is, that the workspace SWITCHER is only displayed at one screen (as the thread title says ...).

You can't drag a window to another workspace on the second screen, because there is no workspace preview for that screen where you could drop that window.

If you want to drag a window from workspace 1/screen 2 to workspace 2/screen 2 it's not possible. You have to move it to workspace 2/screen 1 (this is shown on the workspace switcher), switch there and then move it to the second screen ...
horrible ...

---

### Post by markbl on 2012-07-12
> **mojo2012 said:**
> 
@markbl: di you read the previous posts? michael and me already have this option enabled. Switching itself is NOT the problem - IT WORKS!

Yes, I have. Please read my first post in this thread. Clearly I know you have a different problem! My next post was replying to lolpenguin's one-liner which I interpreted to be about the "classic" gnome-shell dual-screen workspace switching issue. Perhaps I misinterpreted him?

> 
If you want to drag a window from workspace 1/screen 2 to workspace 2/screen 2 it's not possible. You have to move it to workspace 2/screen 1 (this is shown on the workspace switcher), switch there and then move it to the second screen ...
horrible ...
Well shift+ctrl+alt+up/down works on the second screen and is much more efficient than that. Personally, that is how I always move windows between workspaces anyhow, even on the primary screen.

---

### Post by lolpenguin on 2012-07-12
> **markbl said:**
> That's just the default option. If you want it on all monitors then change it by just pressing the button in gnome-tweak-tool/Shell.

No, the problem is that the workspace switcher in the *Activities overview* only shows the primary monitor. *Workspace switching* on all monitors works perfectly.
The only hope we have is to write an extension that either removes the workspace dash thing, or redesigns it / moves it.
(Cinnamon offers an expo style workspace switcher, but this does _not_ show all monitors)

---

### Post by lumpyhl on 2012-10-13
anyone found solution to this? There's nothing about it on the internet, i'm desperate....

---

### Post by nutsy.ben on 2012-12-10
That works.

> **draptik said:**
> the previously described solution by piratefanaz works:

Open dconf-editor > org > gnome > shell > overrides

uncheck the box labeled "workspace-only-on-primary"

i did not even have to restart gnome, it worked right away.

At least it works with an out-of-the-box arch linux with current gnome installed... Your milage might vary with current ubuntu.

---

### Post by markbl on 2012-12-10
> **nutsy.ben said:**
> That works.
It works but that is the old and clumsy way to do it.

Nowadays, gnome-tweak-tool includes this as a simple check-button option.

---

### Post by igal2 on 2013-09-03
k so more than a year has passed since last message... did anyone figure this out?

---

### Post by amoskittelson on 2013-10-08
This fixed it for me: [https://extensions.gnome.org/extension/323/multiple-monitor-panels/](https://extensions.gnome.org/extension/323/multiple-monitor-panels/)

For the record, my answer is related to having only one "Activities Overview"!!!  :D

---

