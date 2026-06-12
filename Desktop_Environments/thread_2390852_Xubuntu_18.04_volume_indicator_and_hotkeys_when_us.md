---
title: "Xubuntu 18.04 volume indicator and hotkeys when using browser?"
date: 2018-05-03
forum: Desktop Environments
---

### Post by amanchesterman on 2018-05-03
Hi everyone, I have Xubuntu 18.04 running on a Dell Studio 1558 laptop. The machine is a hand-me-down from my son and was marketed with a view to watching DVDs etc., so it has stereo speakers and some of the function keys have symbols to control CD or DVD playback (play, pause etc.). In particular, F7 has a symbol to mute the speakers, F8 to reduce the volume, and F9 to increase the volume.

Previously I had Xubuntu 16.04 on it, running very happily for several years. One of the things I liked was that when I installed it, it immediately recognised the volume control function keys. I got into the way of using them routinely when playing music or video online (YouTube and similar sites). I could change the volume using the keys, and when I did so the panel indicator would flash up to show the change.

In 18.04 this doesn't happen. I have both Chromium and Firefox, and with both of them the volume keys don't work and no indicator appears.

However I do have SMPlayer, and when I play music or video files with that the keys operate as they did before. There is no indicator on the XFCE panel but there is a visual indicator (like a progress bar) in the SMPlayer window.

Can anyone advise me how to proceed? For the time being I have added Pulse Audio Volume Control to the panel, and that works fine; but it's not as convenient for me as using hotkeys, and I would like an indicator pop up as well if possible.

Thank you in advance for your help! John.

---

### Post by amanchesterman on 2018-05-06
I did a bit more research and experimented, and solved the issue myself -- so I'm posting the solution here in case anyone else wants to know.

I installed the package **xfce4-volumed**. The volume hotkeys on my laptop now work, and a volume indicator appears when the volume is changed, as it did before. 

I don't know why the package isn't included with the Xubuntu distro. I found a web page which said that it isn't being maintained any more so I guess that's the reason. Anyway, it works fine.

---

