---
title: "Video playback corrupting... sometimes."
date: 2007-10-05
forum: Desktop Environments
---

### Post by SarahKH on 2007-10-05
Got an odd little fault that's appeared since I reinstalled the other day.  I'm using Totem Xine and the Automatix provided non-free/AUD codecs to playback DivX/XviD and such.  Envy has installed the Nvidia drivers.  Basically if I do 'something' then the video playback becomes a static display of technicolour pixels; the sort of thing you get when you video card's blow its RAM; however CTRL+ALT+BKSP and away we go, if I use mplayer -vo x11 <filename> it works fine.

And needless to say it's not a blown video card because it's confined to the overlay area :D 

Anyone experienced this?  I'm thinking it might be either WINE or this iteration of the Nvidia drivers (the only things that have changed) but would like a second opinion.

---

### Post by Lord Illidan on 2007-10-05
Why do you think it is wine? Totem has nothing to do with wine..

---

### Post by SarahKH on 2007-10-05
> **Lord Illidan said:**
> Why do you think it is wine? Totem has nothing to do with wine..

Because I've had it do it having closed apps in wine.  I'm aware that there isn't a direct link between Totem and wine, but I wondered if anyone had seen this happen loaded with the latest stable Nvidia drivers and the latest version of wine.

I'm looking suspiciously at the Nvidia drivers, but not ruling out wine somehow fouling up the video overlay ability. 

Hence... second opinion requested.

Ahh, spotted this in dmesg:

NVRM: Xid (0001:00): 13, 0000 01019700 00004097 00001808 00000000 00800000

Google takes me to a forum and it looks like a bug in the 100.14.19 drivers.  Yay :(

---

