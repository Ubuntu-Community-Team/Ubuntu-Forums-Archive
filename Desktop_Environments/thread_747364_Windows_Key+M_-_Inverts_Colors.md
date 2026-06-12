---
title: "Windows Key+M - Inverts Colors"
date: 2008-04-06
forum: Desktop Environments
---

### Post by ShakataGaNai on 2008-04-06
I'm running a fairly standard copy of Ubuntu 7.10, just gnome, nothing fancy.  Ever since I installed when ever I press the windows key + M - the screen inverts the colors.  Now this is a cool trick and all - but I'd like to know how to stop it.  I can't find this setting ANYWHERE.

Part 2 - I'd like to be able to use the windows key in Ubuntu to emulate windows functionality.  Like Windows+L for lock, Windows+M for minimize.  I've gone into "Keyboard Shortcuts" Prefences and tried with no results. I also went into "Keyboard" Preferences and set my keyboard to 104 Generic (from 105) and set the Alt/Win key behavior under Layout Options.  Still isn't working.

I appreciate the help
-SGN

---

### Post by mcduck on 2008-04-06
That's a feature of Compiz (the "Desktop Effects". If you want to get rid of it, install the compizconfig-settings-manager to get a GUI for configuring Compiz, and then use that to find & disable the "Negative"-plugin.

---

### Post by ShakataGaNai on 2008-04-06
Awesome, now I can indeed press and use Windows+M. 

I tried other key combo's like Windows+D for logout, Windows+L for lock and Windows+R for Terminal.  None of them seem to work.  Are those also magically bound to something else (that seems to have no visible effect on screen)?

Thanks

---

### Post by mcduck on 2008-04-06
> **ShakataGaNai said:**
> Awesome, now I can indeed press and use Windows+M. 

I tried other key combo's like Windows+D for logout, Windows+L for lock and Windows+R for Terminal.  None of them seem to work.  Are those also magically bound to something else (that seems to have no visible effect on screen)?

Thanks

I can't check them right now, as I'm on a Mac at the moment, but if you tried to change them through Gnome's keyboard shortcuts, and they don't work, you could try configuring them in the Compiz settings manager instead. At least at some point Compiz didn't use Gnome's shortcut settings  but had it's own instead, it might have changed with Compiz Fusion, but it's worth a try at least.

---

### Post by ShakataGaNai on 2008-04-06
I looked for one central repo of key bindings, alas there is none.  But  I did find the solution I was looking for:

"Enhanced Zoom Desktop" controls Super+L & Super+R.  So I turned that off and I got the use of Super+R for launching terminal.  Super+L and Super+D (for lock & logoff - respectively) still don't work.  I tried several different experiments using the gnome "Keyboard Shortcuts" preferences, but I couldn't get L&D to work.  Seeing is how I got the two important ones working - I'm happy enough.

Thanks

---

### Post by ~Nightingale~ on 2008-04-06
wait, what? inverting colours? cool, gotta try that some time:)

---

