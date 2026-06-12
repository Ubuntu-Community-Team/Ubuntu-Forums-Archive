---
title: "Dell Studio 1749 sound issues"
date: 2011-04-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by piratemari on 2011-04-20
So I've been running ubuntu on my laptop since I got it, around 8 months ago. I recently upgraded to maverick and it was working perfectly until yesterday. Yesterday I unplugged my usb headset while in a skype call and my computer freaked out, blackscreened, and froze. When I rebooted, the internal speakers had stopped working completely, even though the sound works perfectly on both sets of headphones I have. I've tried most of the fixes that have been presented in other threads and none of them are working, including rebooting the laptop with the headset in. One thread suggested that modifying /etc/modprobe.d/alsa-base.conf by appending the following line to this file would work:
```
options snd-hda-intel model=dell-m6
``` BUT apparently even though my user account is the only account on the computer and has administrator privileges I do not have permission  to modify the file. (It says I am not root, and I do not own the file so I cannot change permissions or modify it.)

I ran the alsamixer diagnostic, here's my link: [http://www.alsa-project.org/db/?f=429351bec35a3fea587c5906aa12dd709385abb4](http://www.alsa-project.org/db/?f=429351bec35a3fea587c5906aa12dd709385abb4)

Any help would be greatly appreciated.

---

### Post by mikewhatever on 2011-04-22
To modify files outside your home folder, a privilege elevation is required, in other words, you have to open the file like so:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

...gksudo is the part that does the privilege elevation.

---

### Post by piratemari on 2011-04-22
Ah, thank you very much for that! However changing the file had no effect. I even tried removing everything but that line and doing that..still no cigar.. this is such an annoying and aggravating issue.

Edit: Okay, I even uninstalled (purged,rather) and reinstalled alsa-base and alsa-utils and it STILL wont work. The alsa-base.conf file has gone back to what it was before I modified it so I know the purge and reinstall actually did something.

However since I purged it I ran a new diagnostic, so here's the link: [http://www.alsa-project.org/db/?f=f5e8e6b409da8c33368e34626fb89f208691d10b](http://www.alsa-project.org/db/?f=f5e8e6b409da8c33368e34626fb89f208691d10b)

---

### Post by mpace965 on 2011-04-30
After changing the file, you need to reboot.

---

### Post by piratemari on 2011-05-01
I have. I rebooted after each change I made. Even upgrading to Natty did not fix the issue, as well as trying to add the code into that file again, and even only have that code in the file, after it upgraded. I'm really at a loss here. I do **not** want to re-install, not only because I have customised this really nicely to my liking, but also because I partitioned my hard drive so that my files are on a different partition and I absolutely do not trust myself to not somehow erase everything through a stupid accident. I really miss listening to things through my speakers. :(

Edit: Also, I should note that I DO have sound before I log in to ubuntu. I hear the little drumbeat when I get to the login screen. As soon as I log in though all sound stops unless I have a headset in.

Edit again: OMG I fixed it!! I was playing with the settings and noticed that suddenly now there are MORE options for the output on internal speakers than there used to be! Sure enough when I changed the settings from the default to Analogue Stereo 4.0 the song I had in the background just started playing.<3 Woot.

---

