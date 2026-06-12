---
title: "gnome-settings and gnome-panel using a lot of CPU"
date: 2005-06-19
forum: Desktop Environments
---

### Post by otherdave on 2005-06-19
Hello all,

I searched briefly before posting this so I apologize if it was covered and I missed it.

I recently switched to Linux (Ubuntu Hoary Hedgehog) as my main OS. I've been running XP in a VMWare session when I need it.

My machine was fairly slow because of this. I only have 512 megs of ram (more is on the way) so I figured my sluggishness was because of that.

However, I shutdown my VMWare image and tried to do some work. My Load Average (via 'top') was showing a load of 8+ (no, I'm not kidding) when VMWare was running and then it calmed down to a cool and collected 6+ (sarcasm!) when VMWare was shut down.

I noticed that the trashapplet, gnome-settings and gnome-panel were using about 30% of the cpu each (again, according to 'top'). I removed the trashapplet from my bar and killed gnome-settings and gnome-panel.

I wasn't aware I was even running 'gnome-settings' so perhaps that's not an application but something in the background that gets used?

In any case, killing all of that has given me a load average of around 0.17 - 0.22 which is super-sweet compared to 8.

Is there a known issue about this? The only thing I have running in my panel that is not standard via the install is Tomboy. I'm running Gaim as well.

Perhaps it's just a fluke but I wanted to check here and see if there was something I should know about.

---

### Post by tread on 2005-06-19
I'd say fluke .. maybe a misbehaving applet. Have you had this problem again? gnome-settings-daemon is something that runs in the background and manages .. well .. gnome settings :). Also its useful if you run gnome apps in some other window manager too. I have tomboy and the trash can applet running without any problems.

---

### Post by otherdave on 2005-06-19
[QUOTE=tread]I'd say fluke .. maybe a misbehaving applet. Have you had this problem again? gnome-settings-daemon is something that runs in the background and manages .. well .. gnome settings :). Also its useful if you run gnome apps in some other window manager too. I have tomboy and the trash can applet running without any problems.[/QUOTE]

I'm only about 1.5 weeks into my Linux usage so I haven't noticed it again. Like I said, I'm using VMWare and since my RAM is limited for the time being I expected some system slowdowns. I'm going to try to keep an eye on those processes for a few days and see if it comes back.

---

