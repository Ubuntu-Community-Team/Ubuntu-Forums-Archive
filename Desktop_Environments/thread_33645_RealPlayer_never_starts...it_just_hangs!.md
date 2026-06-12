---
title: "RealPlayer never starts...it just hangs!"
date: 2005-05-11
forum: Desktop Environments
---

### Post by haldrik on 2005-05-11
Since I tried to install mplayer (quite a while ago), I have been unable to get RealPlayer to work at all. If I type "./realplayer" in the /opt/RealPlayer directory, the program never starts, but the cursor also never reappears, so it seems like its TRYING to get the program started. IN the Process Table I see realplay and three instances of realplay.bin , but no program on the GUI!
Could someone please help? I can't use Helix for many of the streeming sites I like, it always says I need the RealPlayer program (also mplayer, xine, kaffeine only play a certain number of real streams, but not all (maybe only half).
Thanks in advance for any help!!!!
Peace,
Haldrik
ps I've unsinstalled and reinstalled several times, removed mplayer, etc, but nothing works!

---

### Post by Xian on 2005-05-11
You might just need to disable the sound system.
There is probably a conflict.

Sytem > Preferences > Sound [In Ubuntu]
Untick the "Enable Sound Server Startup" box and login again.

KDE Control Panel > Sound & Multimedia > Sound System [In Kubuntu]
Untick the "Enable The Sound System" box.

Also, read [THIS](http://www.ubuntuforums.org/showthread.php?t=32063)  thread for some more info on sound in Hoary.

---

### Post by haldrik on 2005-05-11
(Incidentally , Im using the latest Kubuntu)

Well, that works! Unfortunately, I would really like to be able to have system sounds (like kopete's notifications, window notifications, startup sounds, etc.) as well. Is there a way to have both? I've honestly been thinking about switching from ALSA to the ESD sound system (although I've read that it's inferior) since I believe when I tried that before it worked. 
Anyone have an opinion about 1) getting everything to work at the same time on KDE, or 2) switching to ESD?

Thanks a bundle!

---

### Post by jaclayton on 2005-05-12
I don't know what I've done differently to you, having just installed Kubuntu for the first time.

I've got Realplayer on at the moment (Latest Hitch-Hiker's Guide to the Galaxy in 5.1 surround from the BBC) and get the KDE system sounds just fine.

So I can confirm that it works!  However, I don't have Mplayer installed.  So maybe that's the key.  I'm using the ALSA sound system, by the way.

Not a lot of help, I know.  If I find out *why* it works, I'll let you know!

---

### Post by jiyuu0 on 2005-05-12
i happend to have the same prob... try this:

sudo killall esd

then run realplayer again...

---

### Post by haldrik on 2005-05-12
Well, I finally got it working, thanks for all your help!
The trick was to move the "auto suspend" bar in the KDE Control Center, Sound System to 1 second instead of 0 seconds (I thought zero seconds would actually suspend KDE's exclusive control of audio IMMEDIATELY upon disuse, but instead it seems to not suspend at all unless the bar is set to at least 1 second).
Incidentlally, this cleared up several sound problems: audacity works without killing artsd, so does flash audio within Firefox, and of course, Real Player.
Thanks again for the support!

---

### Post by lark5000 on 2005-05-15
[QUOTE=jiyuu0]i happend to have the same prob... try this:

sudo killall esd

then run realplayer again...[/QUOTE]

AND I had the same problem, and ^this worked.  Thanks!

---

### Post by MrMunson on 2005-05-22
[QUOTE=jiyuu0]i happend to have the same prob... try this:

sudo killall esd

then run realplayer again...[/QUOTE]

Super sweet! Worked like a charm. Do I have to execute that command every time i start the computer now in order for it all to work? If so, what would be the simplest way to automate the process, i.e., not have esd loaded(?) on boot?

---

### Post by Pitbull on 2005-05-31
I too have had problems with Real Player, if it starts at all it freezes or says it can't play a "ram" stream.  

Do I run this in a terminal window?      "sudo killall esd"     That's all?

Also, Audacity won't show "in" and "out" and won't play sound at all.  This whole audio configuation issue is a can of worms and needs to be streamlined if Ubuntu wants to grow in popularity.  Have spent several evenings on this, I suspect the whole issue is tied to the whole set up of audio in general.

Good news, I have Skype working.  Will follow this post and take advice mentioned.  I really want Ubuntu to work for me as it's one of the most pleasant distributions I've tried.

I'll hang in there...

Thank you.

---

### Post by jiyuu0 on 2005-05-31
[QUOTE=MrMunson]Super sweet! Worked like a charm. Do I have to execute that command every time i start the computer now in order for it all to work? If so, what would be the simplest way to automate the process, i.e., not have esd loaded(?) on boot?[/QUOTE]


try this... and u'll never need to kill esd again

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

