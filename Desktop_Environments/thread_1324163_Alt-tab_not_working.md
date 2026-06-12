---
title: "Alt-tab not working"
date: 2009-11-12
forum: Desktop Environments
---

### Post by grkuntzmd on 2009-11-12
I reinstalled kubuntu 9.10 yesterday after screwing up my NVidia drivers. After the install, the alt-tab key combination does not work -- it does nothing.

I checked the KDE system settings->Desktop, but could not see any problems.

Any ideas?

Thanks.

---

### Post by mrboojive on 2009-11-12
Go to System Settings > Keyboard & Mouse > Global Keyboard Shortcuts and select KWin in the drop down menu. Is the shortcut for "Walk Through Windows" set to Alt+Tab? If not, try setting it to Alt+Tab and see if it works.

---

### Post by grkuntzmd on 2009-11-12
It was already set to Alt-Tab.

---

### Post by mrboojive on 2009-11-12
Is the OS recognizing Alt+Tab at all? If you set the Alt+Tab combo to a different action, does it perform that action?

---

### Post by grkuntzmd on 2009-11-12
I changed it to Shift-Ctrl-B and it works. Something is making Alt-Tab not work.

I ran /usr/bin/setxkbmap and now Alt-Tab works. Go figure...

Thanks.

---

### Post by fermulator on 2009-12-01
confirmed -- this has happened on various machines running 9.10 karmic.

All of a sudden (root cause not yet known) the ALT+TAB functionality stops working.  This is terrible :-(

---

### Post by imanumber on 2009-12-07
I'm having the same problem.

KDE user here.  It was working and then it stopped after a few days.  Nothing else seems to be affected.


I can use alt-F2 to bring up the run dialog and ctrl-tab still cycles tabs in the browser, but the combo doesn't work.

If I try to bind something else to alt-tab the program tells me that it is already bound to cycle windows, so it is bound correctly.

Very frustrating.

---

### Post by nyhm on 2009-12-07
I'm familiar with GNOME on Debian, but brand new to Ubuntu (9.10).

I found that with compiz activated (that is, "desktop effects" not set to None), alt-tab ONLY works via one of the compiz-configured application switchers... all of which are nearly intolerable to me.

If I turn off all compiz-supplied application switchers, alt-tab still doesn't work.

I have to completely disable compiz (System->Preferences->Appearance->Visual Effects->None) for GNOME's default alt-tab to work at all.

Is this a known problem/solution? Should a bug be made against compiz, requesting that it pass-through alt-tab to the window manager if all application switchers are turned off?

---

### Post by asciimo on 2010-01-26
Yeah, just happened to me.  Followed by a sudden claustrophobic sensation.

> **grkuntzmd said:**
> 
I ran /usr/bin/setxkbmap and now Alt-Tab works. Go figure...


That worked for me!  Thanks, grkuntzmd.

---

### Post by libor.hudlik on 2010-02-07
Hallo, I'm an Ubuntu user (gnome). Alt+Tab stopped work suddenly - after some update.

This helped me:
> **nyhm said:**
> 
System->Preferences->Appearance->Visual Effects->None

In the Visual Effects there wasn't anything selected. I selected None and the Alt+Tab started to work, then I switched to Normal. Maybe you can select any choice there.

Thanks, Nyhm.

---

### Post by siddukirk on 2010-02-16
Thank You That helped me toooooooooooo !

---

### Post by dE_logics on 2010-02-16
It will be interesting to see the output of xev.

---

### Post by kaos99 on 2010-02-22
Same symptoms here. Also solved by /usr/bin/setxkbmap

Maybe this will help someone in figuring out what happens. Trying Alt-Tab twice with konsole in the foreground:

```
peter@palap2:~$
Display all 295 possibilities? (y or n)
```

A simple dual Tab (without the Alt) gives:

```
peter@palap2:~$
Display all 3386 possibilities? (y or n)
```

---

### Post by Joshisfloyd on 2010-02-24
To fix this I just set the opened up the keyboard shortcuts window and assigned the alt-tab combination to be mute. I told it to overwrite the old combination, and tested the mute combination. It successfully muted the audio so I switched the "Move between windows, using a popup menu" to be alt-tab, and it is back in business.

---

### Post by ster1988 on 2010-10-05
I think this may have something to do with the "rotate cube" option in compiz config manager. I set my visual effects to none, this fixed the problem. I then proceeded to add effects 1 by one until something broke. Alt tab worked up until i enabled rotate cube. After this it was not working. I found that by going to the windows management area of the compiz config manager that you can select application switcher and resolve some conflicting binds. After doing this i have fancy windows manager and my alt tab back.

Hope this helps

-sterling

---

### Post by phoinx on 2011-05-25
> I have to completely disable compiz (System->Preferences->Appearance->Visual Effects->None) for GNOME's default alt-tab to work at all.

Worked for me!

Linux Mint 10 here.
Don't know why alt+tab/alt+F2 stopped working though... Was working fine 1 day ago...

Thanks, nyhm!

---

### Post by nyhm on 2011-05-25
Looks like I'm still subscribed to this thread. Here's my latest report (short version: still broken).

I tried fiddling with Alt-Tab in Compiz (still running Ubuntu 9.10, Compiz 1:0.8.4-0ubuntu2.1). Same behavior as before. Windows blink upon releasing the alt-tab (that's with the most vanilla switcher available in Compiz). 

When Compiz is enabled at all, there is no way to use the default alt-tab behavior (all such controls appear to be captured by compiz). So, I have to completely disable Compiz so alt-tab is tolerable (no blip/flicker), which is unfortunate.

---

### Post by Copper Bezel on 2011-05-25
Blink in what sense? Out of the four basic switchers, all of them have advantages and disadvantages functionally and aesthetically, but you may be encountering a video card issue of some kind, as well. 

Compiz is a window manager, so as such it replaces Metacity, the window manager used when visual effects are set to None. It's not that Compiz is capturing the Alt+Tab, but that there's nothing else to pick it up if it's not used by Compiz.

---

### Post by nyhm on 2011-05-26
Thanks for the input, Copper Bezel. I see how you are describing the relationship between Compiz and Metacity... if I turn on Compiz, I can't get Metacity behavior, because Metacity has been superseded.

I neglected to recount the full details of the behavior. I've tried all the Compiz switchers. The behavior I'm looking for is "standard" Metacity-like Alt-Tab. That is, as I hold Alt and "click" Tab, each window comes to the front. When I release Alt, all the windows are stacked as they were, except that the last one that was brought forward is now on top and has the focus.

There is a Compiz switcher that gives that behavior. However, there is a glitch. When you hold Alt and then begin "clicking" Tab, the windows behave perfectly well. However, upon releasing Alt, instead of the windows just ending up as they now appear, there is a momentary blip, in which I see the screen as it was before I started Alt-Tabbing. (Then it fixes itself and the selected window appears on top with focus, as it should.) The problem is that momentary glimpse of the "old" stacking order before Compiz performs the final re-ordering.

Without any familiarity with the Compiz code (but some understanding of graphic compositing), here's a description that seems like what it's doing: Upon starting the Alt-Tab command, Compiz takes snapshots of all the available windows, in order to rotate them with its compositing code. Each click of Tab recomposites the view with the next window's image buffer on top. However, I would speculate that Compiz is doing all this on a separate image buffer (not actually manipulating the application windows), which I believe is the basic nature of a compositing window manager. The trouble (as it appears) is at the end of the sequence (when Alt is released), the actual application windows are not *really* repositioned. The smoke and mirrors used to perform the compositing illusion is cast aside (revealing the stale window positions), and then the actual application windows are re-stacked.

That might not be at all how it's implemented, but I hope this description assists someone in the know with reproducing, diagnosing, and fixing this annoyance. I'd really like to turn on Compiz.

---

