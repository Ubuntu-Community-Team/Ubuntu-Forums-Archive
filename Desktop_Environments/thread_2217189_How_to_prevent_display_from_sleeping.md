---
title: "How to prevent display from sleeping?"
date: 2014-04-16
forum: Desktop Environments
---

### Post by F3BQ3DP on 2014-04-16
Hello,

I have an Intel NUC running Lubuntu 13.10. I use it as a TV appliance. I use HDMI for video and sound.

I watch Amazon Instant Video in Firefox. After every ten minutes, the screen goes blank and the sound shuts off. When I press a key, both return to life instantly. By then, the video progresses a few seconds.

So, evidently, it isn't the computer entering standby. It is the display being put to sleep. Since I use HDMI for sound too, the sound stops as well.

The power manager application accessible from the programs menu is the xfce4 one. The first time I load it during my session, it says it hadn't been running; would I like to start it? That makes me skeptical anything I subsequently do in it could have an effect. Still, I start it, and I disable all standby, hibernation, and DPMS.

Starting that program also creates a taskbar applet. Right-clicking that gives me the option to switch into Presentation mode, which I select.

I also installed Caffeine, a program that's designed to disable power management when it's desired. Although the examples I saw online show it with a pretty rich GUI, the only option it gave me was to add processes to a screensaver-exempt list. I did so for Firefox.

None of these steps have worked. I'm stuck waking up my display every ten minutes.

I also run XBMC from this Lubuntu instance, and I have **not **had the problem there, no settings tweaks required.

---

### Post by Dreamer Fithp Apprentice on 2014-04-16
Could you be running another screensaver you don't know about? I may be wrong but I think that's possible. You might run synaptic (I'd install it if you haven't done so -- best way to browse the repositories riches imo), search "screensaver" and sort on the status column to look at what may be installed. I'd try disabling any screensavers completely as a test.

---

### Post by F3BQ3DP on 2014-04-25
Thanks. The one hit in Synaptic on keyword 'screensaver', among installed packages, was xdg-screensaver. I disabled this with [FONT=courier new]xset s off[/FONT]. It didn't help.

Any other suggestions?

---

### Post by Dennis N on 2014-04-26
Disable xfce4-power-manager as described here: [http://ubuntuforums.org/showthread.php?t=2206340](http://ubuntuforums.org/showthread.php?t=2206340)

Install xscreensaver and use it to manage power and screen blanking or screensaver start. Power management is in the Advanced tab, and is disabled by default so leave it as is. Display Modes Tab: set to Disabled to have the screen on indefinitely.

At the time, I did test this setup for an hour at least without touching the computer and the screen stayed full-on in Lubuntu 13.10.

Note that I don't see any package named xdg-screensaver show up in Synaptic, let alone installed, so do you have something different than standard Lubuntu 13.10? Where does that package come from?

---

### Post by Dreamer Fithp Apprentice on 2014-04-27
> **F3BQ3DP said:**
> Thanks. The one hit in Synaptic on keyword 'screensaver', among installed packages, was xdg-screensaver.When you click "search" in Synaptic the second text entry box in the little pop-up window is labeled "Look in:" and has a drop down box of choices for different fields to search. Did you have it set to "Description and name"? I imagine you did, but I ask because I find your result surprising. If I understand xdg-screensaver (and I'm only going by the descriptions in synaptic and on their website, so I may not) it isn't a screensaver itself, just a command line utility to CONTROL some other screensaver. So if you checked "Description and name" that would seem to mean you have NO screensaver.  Maybe, as Dennis N is implying, the problem isn't a screensaver but some power management software. So I'd try his suggestion. If that doesn't do it, just to be thorough I'd search in synaptic, name and description, for "power management", and as a seperate search "power manager" (because I don't know if synaptic search uses wildcards to finish stem words)  and see it there were any other possible culprits. If doing that, and the same for "screensaver", "xscreensaver", and any other synonyms you can think of, doesn't suggest anything better and you still haven't solved it try uninstalling all power management or screensaver related programs, including xdg-screensaver, and reinstalling the ones you want, one at a time, using it enough in between reinstalling the programs to see it the problem still exists. Even if the culprit is something you don't want to do without, at least you will have narrowed the question of the cause and have a better idea where to tinker.

> **Dennis N said:**
> I don't see any package named xdg-screensaver  show up in Synaptic, let alone installed, so do you have something  different than standard Lubuntu 13.10? Where does that package come  from?It's in xdg-utils. You were probably searching Synaptic set to search "Name" instead of "Descriptiotn and name". I could wish the description, either in Synaptic or the website, were more explicit on the point but it sounds like it isn't a screensaver but a command line utility that knows how to talk to screensavers. A screensaver straw-boss. Might be handy for scripting, especially if you wanted the script to be portable.

---

