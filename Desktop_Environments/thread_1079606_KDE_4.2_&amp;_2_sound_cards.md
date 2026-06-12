---
title: "KDE 4.2 &amp; 2 sound cards"
date: 2009-02-24
forum: Desktop Environments
---

### Post by Arnaud_B on 2009-02-24
Hi,
I have 2 sound cards (on-board intel & Audigy2) and I would like kde 4 to use the Audigy2 card as default; however, regardless of the settings I set, it always default to the on-board intel card... I managed (sometimes...) to have it use the Audigy card (editing /etc/modprobe.d/sound); however, when I do that I can no longer use my microphone because it unloads all the sound drivers but the one of the Audigy... kind of weird...
Any ideas of how to "simply" make kde 4 use the Audigy2 card while keeping the use of my microphone?
Thanks!
A.

---

### Post by Ubuntiac on 2009-02-24
I found the easiest way was to set all sound output to pulseaudio in system settings -> multimedia. After that I installed pavucontrol (like Kmix on steroids). (it's gnome based and so may install a lot if you haven't installed other Gnome apps)

Open it, click on the "Outputs" tab and set your desired soundcard to default with the dropdown by opening the dropdown to the right of it's name and selecting "Default". Do this for the "Input" tab, too.

If this still doesn't work, get some sound playing in an app. In pavucontrol's "Playback" tab you should see the volume jumping up and down, even if you don't hear anything. Use the dropdown in the same place as the last step but choose "Moove Stream" and then the name of your preferred soundcard.


I can't guarantee this will work for everyone, but it worked very quickly for me to switch from an unused onboard card to my preferred card in 4.2.

Good luck!

---

### Post by Arnaud_B on 2009-02-24
Thanks for your help! I'll be looking into that... Just one more thing: should I understand that this actually is a bug or a lack of implementation in KDE 4 and that this problem has nothing to do with my setup?
A.

---

### Post by Ubuntiac on 2009-02-24
Umm... Well I don't know enough to really say. I'd guess that it probably falls into a mix of misconfiguration based on it being very difficult for the *buntu team to know how everyone's infinite mix of hardware is going to react to KDE's very new and shiny codebase.

I filed a bug on launchpad though, and when I said what fixed it, the bug was marked as Invalid. Make of that what you will.

---

