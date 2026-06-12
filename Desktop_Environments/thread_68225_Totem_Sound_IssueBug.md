---
title: "Totem Sound Issue/Bug?"
date: 2005-09-22
forum: Desktop Environments
---

### Post by jeffreyvergara.NET on 2005-09-22
hello, im using totem to play my video files (.avi,.mpg etc....) it works pretty fine, but i noticed when I drag the time line forward, the audio will be late than the video. I play files with subtitles so I can see wheather or not the audio and video is sync. There's no problem if you watch the file from the start. Im using Breezy so i think this is a bug?

---

### Post by KingBahamut on 2005-09-22
This is totally an opinion but.....I dont like totem much for video use. 

I find xine and vlc to be much better in this regard. You might wanna try one of those. 

apt-get install vlc xine-ui

---

### Post by Hairy_Palms on 2005-09-22
also try installing totem-xine rather than totem-gstreamer, it just works better i find for everythng

---

### Post by logomancer on 2005-10-14
jeffrey, the problem is fixable for Totem. If you change the sound output server from ESD to OSS, this fixes the bug. To do this:

[LIST=1]
[*]Go to **System > Multimedia Systems Selector** in the top menu.
[*]In the Audio tab, under "Default Sink", select "OSS -- Open Sound System". Don't select ALSA, as Totem has problems with it.
[*]Click Close. You're done!
[/LIST]

I really think we should concentrate on fixing problems with totem-gstreamer instead of relying on xine to make it through. It saves people a lot of grief, especially when totem's the default player.

---

### Post by mvfpoa on 2005-10-26
hell!!

esd should not be the default sink... ok, that esound is low latency, but it exist!

Audio and video on ubuntu could be revised...

look... first i can't play my mp3 or videos.... ok, quickly i found the answer... codecs license... (maybe, during the installation, the user could be prompted to download the necessary codecs) and after i got delayed audio due to esd... is it possible to create a default video sink? and send the audio direct to alsa? :) 

Sorry for the inconvenience... but i think obout a new user on linux who wants to try ubuntu... it is so hard to have a good movie played, isn't it?

---

### Post by epb613 on 2005-11-14
I had the same problem. Changing the default sink to OSS made the sync much better for me, but then I switched it to ALSA and the sync was perfect.

---

