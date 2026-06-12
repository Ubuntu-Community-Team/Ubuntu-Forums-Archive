---
title: "workspace switcher gone south"
date: 2009-07-23
forum: Desktop Environments
---

### Post by bwm71 on 2009-07-23
Firefox crashed on my Hardy machine and now my workspace switcher appears really small on my toolbar.  Right after the crash, went from 2 X 2 to 1 row X 2 columns.  I restarted my machine and the switcher is back to 2 X 2, but all of the workspaces appear in the upper half of the switcher with the lower half just white space and inactive.  Kind of like

```
         
         ------------------
         |        |       |
         ------------------
         |        |       |
         ------------------
         |                |
         |                |
         ------------------


```
Any ideas?

---

### Post by mcduck on 2009-07-23
Are you using Compiz (as in having Desktop Effects enabled)?

In that case check your Compiz settings, specifically the desktop sizes under General Options/Desktop Size. for your 2x2 setup you'd want horizontal & vertical sizes of 2, and number of desktops set to 1.

If you aren't using Compiz try removing the applet from your panel and adding it back again (perhaps log out and back again in between, just to be sure).

---

### Post by bwm71 on 2009-07-23
I could have sworn I was using compiz, but I don't see a process running for it (I thought I used to) and none of the packages returned by "aptitude search compiz" are installed.  However, I do have under System->Preferences->Appearance->Visual Effects "Normal" enabled.

In any case, removing and re-adding the applet worked.  That was too easy.  Thanks.

But I'm still confused about the compiz thing.  Based on your reply, I should be using compiz, no?

---

### Post by durand on 2009-07-23
Well, I think what mcduck thought was that only compiz can support multiple rows for desktops which is why you should have had compiz enabled. Maybe it was just a glitch :S

---

### Post by mcduck on 2009-07-23
> **bwm71 said:**
> I could have sworn I was using compiz, but I don't see a process running for it (I thought I used to) and none of the packages returned by "aptitude search compiz" are installed.  However, I do have under System->Preferences->Appearance->Visual Effects "Normal" enabled.

In any case, removing and re-adding the applet worked.  That was too easy.  Thanks.

But I'm still confused about the compiz thing.  Based on your reply, I should be using compiz, no?

Yes, if you have visual effects set to "Normal" you are using Compiz. And it's installed by default.

The reason I talked about Compiz was not because I'd think it's the only WM that supports multiple rows (actually I can't right now think of any window manager that *wouldn't* support multiple rows :D), but because if you use Compiz and use some strange settings for desktop size the Workspace Switcher applet tends to glitch and use layouts as described by the OP.

---

### Post by durand on 2009-07-23
Fair enough though I don't understand how the OP has desktop effects enabled without any compiz packages.

---

### Post by mcduck on 2009-07-23
> **durand said:**
> Fair enough though I don't understand how the OP has desktop effects enabled without any compiz packages.

If he uses Hardy, Compiz is included by default.

Probably the reason it didn't show as installed is because he tried searching for it with Aptitude, which doesn't always register correctly packages that weren't installed with Aptitude in the first place.

I generally don't really trust Aptitude, it just isn't as reliable as apt-get and sometimes tries to be smarter than it really is, resulting in rather nasty situations. (last time I used it I installed KDE with it, and afterwards when I tried removing KDE again Aptitude wanted to remove most of my graphical apps with it, including stuff that definitely wasn't installed with KDE like Firefox, OpenOffice & Inkscape. Luckily I noticed that before continuing, but I haven't touched aptitude after that, there really isn't any reason now when apt-get has the "autoremove"-option as well.)

---

### Post by durand on 2009-07-23
I find aptitude to be a lot cleaner, though I do know what you mean about acting smarter than it is..

---

### Post by bwm71 on 2009-07-23
Sorry for all of the confusion.  I do have compiz installed.  When I searched for installed packages, I was on a box with a server install of Hardy.  Oops.

---

