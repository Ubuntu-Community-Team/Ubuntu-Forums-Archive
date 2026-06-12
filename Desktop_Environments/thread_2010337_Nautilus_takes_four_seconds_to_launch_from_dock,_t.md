---
title: "Nautilus takes four seconds to launch from dock, two from terminal"
date: 2012-06-25
forum: Desktop Environments
---

### Post by Gullible Jones on 2012-06-25
If I launch Nautilus from the Unity dock (either 2D or 3D), the window takes two seconds to appear and two to show all the files/directories.

If I launch it from a terminal (any terminal, as limited user) it appears and shows everything in 2 seconds or less.

This is reproducible any number of times, with Nautilus already having run (and thus cached). Turning off Unity/Gnome's handling of the desktop background does not fix it.

This isn't a huge deal, but when you're doing file management stuff, four-second delays accumulate fast. It's also especially incongruous because everything else is snappy.

Any ideas what might be happening?

---

### Post by CrocoDuck on 2012-06-25
Hi. As always, everything is slower if done from graphical environment. That's why a lot of people use the powerfull tools of unix command line to work: commands can concatenate a lot of istructions that needs gazillion of clicks to be done graphically. And graphically the same istructions need more steps to be executed.

Of course 2 seconds of delay looks odd, as you are using a terminal emulator in a DE. Have a look at your launcher. It should be located in /usr/share/applications. Find the launcher you are usually click and then have a look at its properties. Look if at the field "command" is simply passed the command "nautilus" (maybe written as nautilus%U). Maybe the default launcher uses some slowing options (actually not on my installation). If so you can try to add a launcher for nautilus that uses only the "nautilus" command. On gnome3 I'm usually copy an existing launcher and then modify it on a root nautilus session by editing its properties.

---

### Post by Gullible Jones on 2012-06-25
Yeah, the entries in /usr/share/applications don't have any unusual options being passed to Nautilus.

> **CrocoDuck said:**
> Hi. As always, everything is slower if done from graphical environment. That's why a lot of people use the powerfull tools of unix command line to work: commands can concatenate a lot of istructions that needs gazillion of clicks to be done graphically. And graphically the same istructions need more steps to be executed.


I'm sorry, I don't think I understand that. Why would a graphical launcher start any application *perceptibly* more slowly, unless it was doing some funny business of its own?

Also, this issue did not exist on Ubuntu 11.10 - only on 12.04.

---

### Post by CrocoDuck on 2012-06-26
> **Gullible Jones said:**
> Yeah, the entries in /usr/share/applications don't have any unusual options being passed to Nautilus.



I'm sorry, I don't think I understand that. Why would a graphical launcher start any application *perceptibly* more slowly, unless it was doing some funny business of its own?

Also, this issue did not exist on Ubuntu 11.10 - only on 12.04.

I'm not an english native speaker, so is hard for me making good sentences... Delays are expected in those things when using DEs; but are expected, as you know, shorter (I'd say milliseconds: *imperceptible* ). Looks odd that you have to hang for 2 seconds, as nautilus is called "directly". So we have to understand what happens. Maybe running htop while launching can say about processes involved in launching, but point out something could be hard... Is that an issue common with all programs or happens only with nautilus?

---

### Post by Gullible Jones on 2012-06-27
Ah, sorry about that.

Anyway this is mostly solved, though I'm not sure exactly what solved it. I did the following:
- Installed zram-config
- Set swappiness to 1
- Put /tmp on a tmpfs filesystem (this shouldn't help, lsof says nautilus does nothing in /tmp)

Nautilus now starts as fast from the dock as from the terminal, though that's really not very fast. There's also still an annoying delay when it starts for the first time, but I suspect that's due to shared library bloat that I can do nothing about.

Edit: turning off irqbalance also helps a bit.

---

### Post by CrocoDuck on 2012-06-28
Yo! So, it looks like you have improved the RAM menagement efficiency in your system and ordered to your system to use mostly the RAM to write informations insted of swap partitions. It should result in a global increase in terms of perfomances and speed.

---

