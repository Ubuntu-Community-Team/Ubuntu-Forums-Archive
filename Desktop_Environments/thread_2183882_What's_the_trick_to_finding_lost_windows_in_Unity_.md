---
title: "What's the trick to finding lost windows in Unity Ubuntu 13.10?"
date: 2013-10-26
forum: Desktop Environments
---

### Post by Jim_Granite on 2013-10-26
I don't know if it's me or if it's Unity, but, in Ubuntu 13.10 (having moved from RHEL6), I can't count how many times in just the past few days I've totaly lost my running applications. They're nowhere to be found. After a half dozen to a dozen clicks, I can "sometimes"  find them, and sometimes not.

We've already covered the specific bug where the Tor Browser Bundle just basically disappears from view, but, now, something as basic as The GIMP is driving me crazy. 

The Gimp, as you well know, is comprised of multiple windows, such as the "Toolbox - Tool Options" and the "Navigation Window", in addition to the editing window.  Whenever I open multiple applications (such as typing this message in Firefox) while using The Gimp, all my Gimp windows but one disappear. So, all I have is the useless-by-itself Toolbox - Tool Options window in The Gimp when I click on the Launcher icon. I click. I click again. I doubleclick. I triple click. I keep clicking.  Eventually I give up on clicking, and just manually close all other windows, and lo and behold, The Gimp shows up (finally!). 

A similar frustration happens with Thunderbird. I can't count the number of times in just the past few days that I've had to kill all the applications on the Unity desktop just to find windows in Thunderbird that I KNOW should be there (as I had not closed them yet). Yet, they disappeared. Almost certainly I'm doing something wrong, but, heck, I've been using PCs since the IBM AT, so, it really should not be this unintuitive to find windows. In fact, half the time, I have to kill Thunderbird and then re-open it to find my window, finally, after a score of clicks, in the Drafts folder. 

What am I doing wrong?
[ATTACH=CONFIG]247283[/ATTACH][ATTACH=CONFIG]247284[/ATTACH]

---

### Post by Frogs Hair on 2013-10-26
You should be seeing indicators next to the open applications in the panel . Gimp now comes with a single window mode, but is not activated by default. I find this helpful on my smaller monitor.

---

### Post by Jim_Granite on 2013-10-26
> **Frogs Hair said:**
> You should be seeing indicators next to the open applications in the panel . Gimp now comes with a single window mode, but is not activated by default. I find this helpful on my smaller monitor.

Thanks. I should have explained that the problem isn't the "indicators" in the case of TOR and The Gimp; but it might very well be the indicators in the case of Thunderbird. I'll keep an eye on them, for Thunderbird.

In the case of Tor, it's just a screwup. For some reason, the Unity browser (which is Firefox) can have its own icon in the Launcher, but the Tor Browser (which is also Firefox, but it's really far fetched to consider them even remotely similar), can't. Huh?

But, what got my goat was "The Gimp". Historically, Gimp has multiple unpinned windows. The probelm with the launcher is that only one pops up when you click on the Gimp launcher icon. It turns out the Gimp is useless without ALL it's key windows. So, as you noted, you have no choice but to put the Gimp into single-window mode, just to work around that bug in Unity:
 [GIMP]Windows->Single Window Mode=on

It's frustrating, but, one by one, we can find a workaround so that each application becomes usable with judicious use of the settings.

---

### Post by Frogs Hair on 2013-10-26
Even before unity and single window mode on gimp I never minimized/closed the tool widows in Gimp so I don't if it was a problem in the past or not. Grab the Ubuntu manual linked in my signature, there is some good information on using hud, dash , and Unity key board shortcuts .

---

### Post by Jim_Granite on 2014-01-03
After 75 days of using ubuntu 13.10 (coming over from RedHat Enterprise 6), I'm starting to get used to the windowing system, some of which is good (and some just a pain with nothing good about it).

One of the bugs in Unity is that it doesn't treat Tor separately from Firefox.

Tor is nothing like Firefox in that when you're using Tor, you're trying to be anonymous, while when you're using Firefox, you're not.

A mistake can be deadly (depending on what you're trying to hide from).

The use-model problem is that Ubuntu 13.10, by default, makes absolutely no distinction between the TBB & Firefox.
(In addition, Unity chooses to hide the all-important Vidalia control panel, which is also important for use with the TBB).

This is a severe use model compromise, that can only be considered a Unity bug since this problem doesn't happen on any other platform, nor on any other operating system.
The ramifications can actually be deadly - depending on whom you are trying to hide from.

In my case, I've only been super frustrated, cursing Unity every time I accidentally enter a URL into Firefox when it's meant for the TBB, simply because Unity is (basically too stupid) to distinguish between the two.

This bug just frustrates me, and makes me wonder what the Unity people were thinking - but - if I were, say, a journalist trying to report on an African dictatorship (or whatever), this severe Unity bug could be deadly. Literally.

---

### Post by buzzingrobot on 2014-01-04
Icons in /usr/share/applications (representing the '.desktop' files) can be dragged into the Launcher.  Does Tor install a .desktop file in /usr/share/applications?  If not, I'd guess the Firefox .desktop file could be copied and repurposed. 

(I don't use Tor.  Does it alter the appearance of Firefox at all, provide some sort of visual clue, so the user can distinguish them? A different theme?)

Thunderbird:  On 13.10 Unity, I keep Thunderbird open in its own workspace.  On occasion, when it is first launched, I've noticed that, for unknown reasons,  it will slide upscreen, leaving only a very narrow strip visible just below the panel.  This strip becomes visible in the adjacent workspace. While it is easy enough to move it back down into view, on a few occasions it has moved upwards entirely out of the way, leaving no trace at all on screen in its workspace. I havent' bothered to chase this down; a "Super+W" spreads all open windows across the screen and I find it there.

---

### Post by vanadium on 2014-01-04
> **Jim_Granite said:**
> 
But, what got my goat was "The Gimp". Historically, Gimp has multiple unpinned windows. The probelm with the launcher is that only one pops up when you click on the Gimp launcher icon.
In the earliest Unity versions, all application windows would come to front when you clicked the icon in the laucher. That was indeed very good with Gimp in multi-window mode. I also liked that with nautilus: one click and all open nautilus windows would be on the foreground.
You probably know that a second click will expose all gimp windows, from which you could quickly switch to the needed one, but yes, it are extra clicks. The fundamental problem is: applications are designed differently, and no single task switching concept fits well to all these designs at once.

---

