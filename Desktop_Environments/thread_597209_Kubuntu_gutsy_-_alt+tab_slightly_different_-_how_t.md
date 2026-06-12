---
title: "Kubuntu gutsy - alt+tab slightly different - how to change back?"
date: 2007-10-30
forum: Desktop Environments
---

### Post by BlueNoteMKVI on 2007-10-30
I just installed Kubuntu 7.10 on my laptop.  I'm loving it, except the pesky alt+tab behavior that I can't seem to fix.

On 7.04 on this laptop, and the same on my desktop box, alt+tab always goes to the previous active window on a desktop regardless of what else is up.  If I hold down alt and push tab several times it cycles through all open windows on that desktop until I release the alt key.  This is the way I'm accustomed to working and I'd like to keep it that way.

Using 7.10 on the laptop (haven't upgraded the desktop box yet) alt+tab always cycles through all windows on the desktop.  This makes it more difficult to find the specific window I'm looking for.  I found the setting in KDE system settings but it just says "walk through open windows" and is set the same way as it is on my desktop (7.04) box.  I'm not using compiz/fusion/beryl or any of that.  I tried it and the wiggly windows were fun but screwed up other shortcuts so it wasn't worth the hassle.

Just to be clear, an example.  I normally have at least Thunderbird, FireFox and Quanta running.  Usually I'm working on a site for a client, so I'll read their email in Thunderbird, edit the site in Quanta and check it in FireFox.  This often involves lots of alt+tab switching between Quanta and FireFox to get it just right.  Under 7.04 if I switch from Quanta to FireFox, release the tab key, then alt+tab again, it goes immediately back to Quanta.  Another alt+tab and I'm back to FireFox.  I can do this back and forth as many times as I want, Thunderbird stays running in the background but never comes to the front.  If I want to bring up Thunderbird I have to hold down alt and hit tab twice to get Thunderbird to come up.

Under 7.10, with the same three windows open, it behaves differently.  If I'm looking at Quanta and alt+tab I might end up at FireFox.  If I release alt, then alt+tab again, I end up at Thunderbird.  I have to alt+tab yet again to get back to Quanta.  Every alt+tab cycles to the next window in line rather than the previously open window.

That's a rather simplified example.  I often have 8-10 windows up at one time doing various things but I only need to really work with two of them.  Sifting through to find the one that I need is annoying and a waste of time.  How can I set the alt+tab function back the way it was in 7.04?

---

### Post by BlueNoteMKVI on 2007-11-08
I eventually found the solution to my problem.  I'm not sure how to change this through the GUI tools, but you can go through the command line and edit this file:
~/.kde/share/config/kwinrc
Find the line that says:

AltTabStyle=KDE

In my file it had "AltTabStyle=CDE" (C, not K) which apparently caused the alt+tab to work the way I described above (always cycling through all windows in the order they were created).  By changing it to KDE it works the way I want it to, flipping back to the most recently used window.  It also shows me a display of all open windows on that desktop so I can choose which one I want.

---

### Post by samwyse on 2007-11-08
It's in System Settings / Window Behavior. There's a "show window list" tick box.

---

### Post by mohamed_fawzy21 on 2008-01-03
I had this problem before,
All what you have to do is to right click the window and go to window behavior under focus press a tick on "Show windows list while switching windows", and it should work.

---

### Post by ~LoKe on 2008-01-03
> **mohamed_fawzy21 said:**
> I had this problem before,
All what you have to do is to right click the window and go to window behavior under focus press a tick on "Show windows list while switching windows", and it should work.

Did you bump a two month old thread to post a solution that was already mentioned? O_O

---

