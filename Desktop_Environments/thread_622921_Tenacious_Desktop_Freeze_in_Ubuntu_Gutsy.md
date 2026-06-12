---
title: "Tenacious Desktop Freeze in Ubuntu Gutsy"
date: 2007-11-25
forum: Desktop Environments
---

### Post by Wienerschnitzel on 2007-11-25
I hope somebody can help me out with this one, because I can't seem to figure out what's causing these freezes. 

I installed Gutsy on my laptop around six weeks ago and, after the initial period of tweaking and figuring out my own  tricks, everything was running smoothly. I had no problems whatsoever, and the system was running more smoothly than it ever had done under XP.

I think it was last Tuesday that I started to experience the freezes. Basically what happens is that the whole desktop environment freezes up. I can still move the cursor, execute a single command in the terminal and switch tabs in my browser, but the rest seems frozen in time. The load bars on my system monitor freeze in place, video and audio will freeze and OpenOffice doesn't respond. 

Then, after between five and forty-five seconds, the freeze is over and everything resumes again. Video and audio resume playback, but it seems that the track keeps moving during the freeze. So if the freeze happens at t=1:42:50 and lasts thirty seconds, the video will resume at t=1:43:20. Also, text typed while the desktop is frozen will show up as a burst of text after the freeze has passed.

Same goes for IM through Pidgin, everything I type will be sent in a single burst after the freeze has passed.

Anyway, enough backstory. This should give you an idea of what's going on. Now, like the good struggling end-user I am, I called my friend and Ubuntu go-to guy and asked him what I could do. He sent me a shell script which, when run, did a system diagnostic. I managed to execute the script during a freeze, and this is what it turned up: 

[ATTACH]51342[/ATTACH]

[ATTACH]51341[/ATTACH]

Now for a little confession: I don't make a habit of checking the updates that the update manager recommends I install. So I may have installed a recent update that didn't jive well with my system, causing these problems as a result. I can, however, assure you guys that I didn't install any significant programs or third party ****, nor did I tinker with the OS myself.

The first diagnostic was made before I took any action, and the results had my friend thinking compiz must be the culprit. I then got rid of every installed component of compiz that turned up in the Synaptic Package Manager and rebooted. He told me to test this first, just to see whether the bug was still there. Turns out that it was. 

The next course of action was disabling the restricted NVidia drivers I've been running to see if that would help. I turned them off and rebooted, and for a while, things seemed fine. I was able to watch a movie without being interrupted, but last night the freeze reared it's ugly head again. This morning I caught it in the act and did a quick system diagnostic, which can be found here:

[ATTACH]51344[/ATTACH]

[ATTACH]51343[/ATTACH]

I'm at a loss. I have no idea what's causing this. I can only imagine it's a conflicting update, but which one? Seeing as it's a recent problem, I don't know what else it could be; my laptop functioned perfectly fine until early this week. I remember being prompted to install a whole slew of updates which I naturally did without thinking it through, but I don't remeber which ones they were and when that was. I only know that the problems started somewhere after that.

I hope somebody can help. My system has frozen repeatedly while typing this post, and I can't work like this. I don't want to have to go back to Windows.

---

### Post by hibernate on 2007-11-25
I'm having the same troubles. I have Gutsy installed on friday and had these troubles 2 times (but i didn't wait enough for system to continue working - pressed reset). This is really strange. I'm now searching the solution over the internet. Hope i'll find anything.

---

### Post by Wienerschnitzel on 2007-11-27
Anybody have any idea what's going on here? This problem is quite the annoyance. I'd love for somebody with more Ubuntu knowhow to take a look at my plight.

In other words: bump.

---

