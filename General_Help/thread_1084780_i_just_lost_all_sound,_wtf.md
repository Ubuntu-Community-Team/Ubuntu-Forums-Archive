---
title: "i just lost all sound, wtf"
date: 2009-03-02
forum: General Help
---

### Post by c/Kr3t on 2009-03-02
my sound worked perfectly till my lady started pushing buttons, she pushed the mute button on my keyboard thinking it would turn the computer off (she uses a mac, give her a break). Thing is, that didn't mute my sound, so she pushed it again at my request and i told her how to turn off my computer. 

Now today I get on and wanna listen to some music but I get no sound at all. I thought at first that we had just macked so hard that we broke my stereo but no, that still plays sound from my xbox. then i thought, maybe it's just the channel is messed up so i switched my computer audio to a different channel but it still doesn't work. so then i thought that maybe it's just on a different setting so i went to system > pref > sounds and changed all those menus to everything on there one at a time but nothin worked.

so now i'm stuck here, without sound.  any suggestions?

---

### Post by c/Kr3t on 2009-03-02
just fixed it, apparently when you press a mute button on your keyboard, it tells pulseaudio to lower ALSA front:1 to 0  obviously   but pressing it again doesn't raise it. so going into the volume control panel and raiseing it will fix it.    they should fix that bug.

---

