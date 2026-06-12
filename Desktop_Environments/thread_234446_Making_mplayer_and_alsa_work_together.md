---
title: "Making mplayer and alsa work together"
date: 2006-08-11
forum: Desktop Environments
---

### Post by buntumaddy on 2006-08-11
Dapper has been great for my Dell Inspiron 8600 notebook and I have managed to get almost everything working, including Wifi, XGL/Compiz, Firefox multimedia etc. All codecs have been installed fine and videos of most formats play great in Totem. Many thanks to the developers and community for such great resource.

Only issue remaining to be solved is playing .mov and .flv files in MPlayer. Mplayer is the my choice for playing videos but I've been having problems with it's Audio setup.

ALSA works great for other applications like Rhythmbox and Totem but for some mysterious reason, isn't working for MPlayer. The default setting is Alsa with default device, channel, mixer. Whenever I try to play a video, it gives me an error **"Could not open/initialize audio device -> no sound"**. Video plays great.

Changing the device to hw=0.0 plays audio and video fine but keeps giving repeated popups saying **"alsa-control: mixer attach default error: No such device"**.

Changing audio setting to OSS, the video lags significantly from the audio. Have tried almost all combinations of audio settings but one problem or the other persists.

As suggested in [this]("http://www.ubuntuforums.org/showthread.php?t=142161") thread, I've tried disabling esd from System->Preferences->Sound and then restart, but in vain. Situation remains the same.

I would also like to mention that at home, I use my Logitech USB Headset 350 and it works good enough, but same problem persists in that too. At work, I use the standard headphone jack. Both sound cards are functioning perfectly fine for all other applications except MPlayer.

Any indication of what the problem could be or how would that be solved is much appreciated. I have decent rapport with linux in general and am very comfortable using the shell. So, please be comfortable about any suggestions as technical stuff will definitely not scare me off. TIA

---

