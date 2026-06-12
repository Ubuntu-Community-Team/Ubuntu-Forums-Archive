---
title: "Permanent killall esd?"
date: 2005-05-25
forum: Gaming &amp; Leisure
---

### Post by Curlydave on 2005-05-25
The effects of "killall esd" only last until reboot. Is there any way to fix this? (So i get sound in ut2k4) thanks!

---

### Post by Xian on 2005-05-25
From the main panel:
System > Preferences > Sound

Untick the "Enable Sound Server Startup" box.

---

### Post by Curlydave on 2005-05-25
thanks!!!

---

### Post by jdong on 2005-05-25
<SARCASM>You'll lose what you love the most: Those little GNOME sounds when you log in and out, and those wonderfully annoying IM noises in the middle of writing a 20-page research essay at the last minute :)
 
</SARCASM>
 
Oh, darn.

---

### Post by Xian on 2005-05-25
I'm testing the system sounds set to some Ramones' licks. 
Uh...it's a little "different".

 :)

---

### Post by arrizaba on 2005-05-26
You do not need to "killall esd" in order to play ut2004. You can configure the machine to operate with multiple sounds from ALSA and ESD. Take a look at the forum:

[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=32063&highlight=sound+esd+alsa[/COLOR]

or the ubuntu guide at:

[COLOR=Blue]http://ubuntuguide.org/[/COLOR]

It worked with me...so I hope it helps you too.

---

### Post by theerga on 2005-05-28
i like the killall option all those other sounds are just annoying. what i find intresting is that many games wont even start or will crash without the killall comand being done. it also well freeze xmms until you do it. so the perma killall is nice for me.

---

### Post by NeoChaosX on 2005-05-28
[QUOTE=arrizaba]You do not need to "killall esd" in order to play ut2004. You can configure the machine to operate with multiple sounds from ALSA and ESD. Take a look at the forum:

[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=32063&highlight=sound+esd+alsa[/COLOR]

or the ubuntu guide at:

[COLOR=Blue]http://ubuntuguide.org/[/COLOR]

It worked with me...so I hope it helps you too.[/QUOTE]
The thing is, there are still programs that refuse to produce sound if the ESD daemon is running, even if you have ALSA set up correctly (Tuxkart, Clanbomber are just two examples). You have to disable the sound server to get it them to work.

---

