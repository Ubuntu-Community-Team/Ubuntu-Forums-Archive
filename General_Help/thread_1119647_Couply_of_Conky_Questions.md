---
title: "Couply of Conky Questions"
date: 2009-04-08
forum: General Help
---

### Post by dethredic on 2009-04-08
So, I never really had room on my desktop for a conky, but I have shifted my habits and started experimenting with it.

1) Hotmail Script. I just want something to check how many new messages I have in my inbox.

2) My Gmail script is pretty slow to update. For it I am using:
${execi 300 python ~/scripts/gmail.py}
Script itself shouldn't be a problem because I can run that and it updates instantly. Is that 300 in seconds? Because 5 minutes seems to be about right for update time.

3) More advanced MPD usage. Currently I have:
MPD: $mpd_title - $mpd_artist
That works great when it is playing, but if I pause or stop MPD I would like the "$mpd_title - $mpd_artist" to change to either paused or stopped. I am sure this would work with if statements, but I am unsure as to how the syntax works.
This would be the key variable: mpd_status

Currently I have my conky centred on the bottom of my scree. Can I make the "$mpd_title - $mpd_artist" be like an anchor, so if that sting become longer it will expand to the right and not reposition everything?

4) This one is even smaller, but for my time I get "April 07 09:39"
${time %B %d} ${time %I:%M %P}
Is it possible to get it to display without the useless 0's? (April 7 9:39)
Also for my CPU usage can I make it 05% so it doesn't keep jumping as well. I am currently using this:
{cpu cpu0}

---

### Post by dethredic on 2009-04-10
anyone?

---

### Post by dethredic on 2009-04-11
final pity bummp

---

### Post by VCoolio on 2009-04-11
Hi, didn't see your thread until now. The 300 is seconds indeed. For email check [this]("http://ubuntuforums.org/showthread.php?t=869771") thread. Hotmail uses an ancient protocol and will not show new message count according to that thread. The mpd thing: start with 
${if_running mpd} 
and then just your working code. Close with ${endif}. Fill in for mpd the name of your mediaplayer (check your system monitor for the name of the process). This will not work for banshee (process name banshee-1) as conky will start banshee if it is not running and you don't want that. If your player is not running, nothing will be displayed. If you want something like "mpd not running" message, use the same but close with:
${else}${color}mpd not running ${endif}.
For the time formatting [this]("http://manpages.ubuntu.com/manpages/intrepid/man1/date.1.html") may help.

---

### Post by dethredic on 2009-04-12
> **VCoolio said:**
> Hi, didn't see your thread until now. The 300 is seconds indeed. For email check [this]("http://ubuntuforums.org/showthread.php?t=869771") thread. Hotmail uses an ancient protocol and will not show new message count according to that thread. The mpd thing: start with 
${if_running mpd} 
and then just your working code. Close with ${endif}. Fill in for mpd the name of your mediaplayer (check your system monitor for the name of the process). This will not work for banshee (process name banshee-1) as conky will start banshee if it is not running and you don't want that. If your player is not running, nothing will be displayed. If you want something like "mpd not running" message, use the same but close with:
${else}${color}mpd not running ${endif}.
For the time formatting [this]("http://manpages.ubuntu.com/manpages/intrepid/man1/date.1.html") may help.

Thanks, although I was thinking something more like:

If mpd_status = running then mpd_artist - mpd_song
elseif mpd status = paused then 'paused'
else 'stopped'

I just looked at the variables and it doesn't look like they have something like that.

---

