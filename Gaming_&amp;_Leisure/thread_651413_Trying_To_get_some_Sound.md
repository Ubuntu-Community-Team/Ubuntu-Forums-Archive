---
title: "Trying To get some Sound"
date: 2007-12-27
forum: Gaming &amp; Leisure
---

### Post by PPAAUULL on 2007-12-27
Ok so I am trying to get game sound from a Quake3 game aswell as teamspeak and I have looked a round and found some good howtos the only problem is that when I issue the command that many of them suggest I get an error.

So I issue ```
sudo echo 'quake3.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
```
and I get an output of ```
bash: /proc/asound/card0/pcm0p/oss: Permission denied
```

Does anyone know why this is and if there is a way to fix it or change the file anotherway?
Thanks

PS I have tried editing it manually and I get a whole other set of problems.

---

### Post by BreathEasy on 2007-12-27
Ok, here's the technical reason for why it fails: although the sudo is allowing you to run the echo command at a higher permission, the redirect (ie. everything after the >) is not being contained within the sudo, which basically means that echo is running as root, but the /proc stuff is not. You need everything on the line run as root.

The easiest solution is to do this: in the terminal, type:

sudo -s

This will launch a shell with full root access. Type in the original command without the sudo (although it doesn't really matter here):

echo 'quake3.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss

Type **exit** and then you will fine Q3 to run with sound. To make this permanent so that the fix works after you reboot, type in

sudo gedit /etc/rc.local 

Before the line which says "exit 0", add the "echo quake3..." line as above into the file - don't put the sudo in however. Save, and you're good to go. :)

---

### Post by PPAAUULL on 2007-12-27
Ok so I did and I still start TeamSpeak and then my ET Mod and there is still no sound. And yes I did add the one for ET aswell but it doesn't give me sound when I am on Teamspeak at the same time. anyone have any ideas?

Thanks

---

### Post by BreathEasy on 2007-12-27
Hrm. Try using double-quotes instead of single quotes in the echo line. ie:

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Do you get any sound at all? Try just Q3 first. If that works, enable Teamspeak. To be honest, if it fails after Teamspeak them I'm not surprised - the problem with OSS is it ties up the sound channels with the one program, so another program trying to use the sound will fail, which is why ALSA was created. Sorry. :(

---

