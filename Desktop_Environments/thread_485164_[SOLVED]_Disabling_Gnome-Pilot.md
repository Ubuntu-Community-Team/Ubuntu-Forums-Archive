---
title: "[SOLVED] Disabling Gnome-Pilot"
date: 2007-06-26
forum: Desktop Environments
---

### Post by galvao on 2007-06-26
Greetings.

I'm trying to access my palm in my Ubuntu 7.04. I've found JPilot, which is a very nice software but I wasn't able to sync my Palm, so I've contacted the author.

He replied to me saying that JPilot and Gnome-Pilot are in conflict, that I can't use both at the same time, so he asked me to disable Gnome-Pilot.

How can I do this? I've tried uninstalling it, but Synaptic then tells me it will uninstall ubuntu-desktop too (heh).

Any tips?

TIA,

---

### Post by canadianwriterman on 2007-06-26
Don't worry, ubuntu-desktop removal will not have a negative effect. I know it looks scary, but go ahead and uninstall gnome-pilot. Your desktop will not be removed. You do need ubuntu-desktop for version upgrades of Ubuntu, so you can use Synaptic to reinstall later.

---

### Post by galvao on 2007-06-27
So, on a related topic: I can also uninstall Evolution without having any problems then?

I should only re-install ubuntu-desktop afterwards.

Have I got it right?


Thanks,

---

### Post by galvao on 2007-06-27
Ok, there's a weird problem happening here:

I just can't re-install  ubuntu-desktop WITHOUT re-installing gnome-pilot as well - Synaptic don't let me do it - so this solution just don't fit. ](*,)

Please advise.

TIA

---

### Post by kgr132 on 2007-07-25
I have both gnome-pilot and J-Pilot installed and J-Pilot works just fine. That deal about uninstalling gnome-desktop scared me too, so I left gnome-pilot alone. I don't have gnome-pilot starting up at all, though. No session startup program entry or panel applet or anything like that, either. Try running 

sudo killall gpilotd

in a terminal window. If it responds with no process killed, then gnome-pilot isn't / wasn't running and it's likely it isn't causing any trouble. If the command gives no response, then you just killed gnome-pilot and maybe your J-Pilot sync will work now. My problem with J-Pilot was related to the port it wanted to use to sync to my USB cradle. See my other post about that here:
[http://ubuntuforums.org/showthread.php?p=3076255#post3076255](http://ubuntuforums.org/showthread.php?p=3076255#post3076255)

Good Luck.
-K-

---

### Post by galvao on 2007-07-26
Yeah, actually I don't know exactly what happened anymore, since I just tried to run JPilot again and everything ran fine.

I was probably too stressed out to notice something. Sorry for this #-o

---

