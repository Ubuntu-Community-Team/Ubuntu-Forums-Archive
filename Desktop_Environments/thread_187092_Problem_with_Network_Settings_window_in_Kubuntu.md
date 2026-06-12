---
title: "Problem with Network Settings window in Kubuntu"
date: 2006-06-02
forum: Desktop Environments
---

### Post by mwneal on 2006-06-02
Hey all, I'm something of a noob to Linux systems, so go easy on me. :)

Anyway, I'm configuring Kubuntu Dapper for wireless (yes, a Broadcom chipset...no, I don't think I need help with the actual setup), and it's mostly set up. I just have to configure the wlan0 interface to connect to my wireless network...now here's two problems I run into.

First, I go to K > System Settings > Network Settings, and I see my eth0 and wlan0 configurations there, and that I have to go to Administrator Mode to modify settings. Thing is, I maximize the window, remove the panel and toolbar, and yet apparently my resolution ( 1024x768 ) is STILL not big enough to show the buttons...

So I try an alternative. From the panel, I go to System > Settings > Internet & Network > Network Settings. With some window resizing and panel-hiding, I see the Administrator Mode button. Yay! So I press the button and all of the configuration settings disappear, replaced instead with a red border around where they should be. There seems to be no way to actually access the settings now. Funny thing is, I wasn't even prompted for a password or anything, and I know I haven't tried to access anything as root for this session.

So I need help getting to these settings! If you could provide me with another alternative to accessing these settings, whether it be via GUI or Console, it would be much appreciated. :)

---

### Post by megadodo on 2006-06-02
Hi
Try kcontrol instead (type "kcontrol" into a konsole.) Its the old interface to the settings, and I find it much more reliable than System Settings.
But dont hold your hopes out for knetwork settings. Ive always just given up with it and edited the config files by hand, but it may work for you!
Good luck
Rich

---

### Post by mwneal on 2006-06-02
Hey megadodo, thanks a lot, I can get access to things now! Now I just hope I can get my WLAN working when I get home. :)

---

### Post by Ptero-4 on 2006-06-02
The disappearing buttons thing is IIRC a bug from Breezy which was going to be fixed on Dapper, but it seems to still be there.

---

