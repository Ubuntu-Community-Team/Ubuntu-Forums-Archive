---
title: "Bottom panel not showing tasks/windows"
date: 2007-03-26
forum: Desktop Environments
---

### Post by Ubunthree on 2007-03-26
I started with Ubuntu (Edgy) a few weeks ago, and am working through the usual noob issues. I've gotten most things working satisfactorily at this point, but one odd new thing has come up which I need to fix:

When I open a window or start an appliction, the corresponding label for it no longer appears on the bottom panel (what would be the "taskbar" in Windows). So, I can't bring a covered window up to the top by clicking its panel label. Worse, if I minimize something, the window collapses as usual down into the panel, but there still is no label for it there, and I have nothing to click on to bring it back up again. It will show up in System Monitor as "Sleeping," and I can end or kill it there, but can't bring it back up again.

Things which I've already tried, which haven't helped:
- Shutting down/restarting
- changing themes
- entering [COLOR="DarkRed"]metacity --replace[/COLOR] in a terminal

Recent system history:
- A few days ago I swapped out my old NVIDIA Vanta card for a friend's slightly less old GEForce. It was missing its fan, so I ran the computer with the case open and a big window-fan blowing in, just to be safe. Everything fine.
- This afternoon I saw that ancient derelict computer of mine had a CPU fan that was the right size, so I stuck that on the GEForce, saw it running, and closed the case back up again. Everything fine.
- Also this afternoon I started the Update Manager downloading another 50 meg or so of updates, which takes a looong time with my dialup connection. It got close to the end and then lost server connection. It informed me that some packages hadn't been downloaded, and asked if I wanted to continue anyway, and I said "yes." Partway through the installation process, the progress bar stopped, and the Details window showed a black bootup-screen-like display which appeared to be frozen partway through an Evolution update. I could type in this window but could make nothing happen. After about twenty minutes with nothing happening, and no response from anything, I had to restart. Some time after this I noticed that a terminal window which I had minimized had disappeared, and then I saw that NO windows were available from the bottom panel. Exactly when this happened I can not say. And I don't remember now exactly which update packages I had chosen; I'm doing a bit of it every day.

Any help on this would be appreciated. Please be aware that if you tell me something like, "Recompile your kernel" or "Reinstall X" or something, I'll need to be told how to do that, as my noobness is both deep and wide.

Thanks!

---

### Post by murlosad on 2007-03-26
You might be overcomplicating your problem.  Did you try adding the Window List back to the panel?

Right click on the bottom panel >> Select 'Add to Panel'

Under 'Desktop and Windows' select 'Window List' and press add.

See what that does.  If that still doesn't work, you may need to try updating gnome to make sure you have all the right versions of the different dependencies.

type > sudo apt-get upgrade gnome into a terminal window.

Applications >> Accessories >> Terminal

---

### Post by Ubunthree on 2007-03-27
Thanks, murlosad!

- [COLOR="DarkRed"]Add to Panel[/COLOR] added another little sliding grab-handle-thing to the panel, but the Window List itself was still hidden. Tried it again, and got another of the same, so the item was being added, just not displaying correctly.

- [COLOR="DarkRed"]sudo apt-get upgrade gnome[/COLOR] gave me an error, something about a package not being completed or something - sorry for not making a note of it exactly - which I suppose was fallout from the interrupted update earlier. But, it did tell me what I needed to enter to do the upgrade manually. Copying/pasting *that* finally set things in motion, and in a minute or two I had three normal window-lists on the panel. Deleted two of them, and things are back to normal.

The ability to get help with things like this so freakishly quickly has become one of Ubuntu's main selling points for me. Thanks again.

---

### Post by murlosad on 2007-03-27
glad I was able to help at least a little bit, and happy that you fixed the problem.

Enjoy Ubuntu.

---

