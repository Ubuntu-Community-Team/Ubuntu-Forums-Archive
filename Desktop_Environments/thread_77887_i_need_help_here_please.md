---
title: "i need help here please"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Llewxam on 2005-10-17
been trying to work with totem since wednesday. tried to update the plugins for it and i have had no success whatsoever. in general (when i try to play mp3's, mpgs, dvd's or any other media i get this kind of error: There were no decoders found to handle the stream in file file:///media/windows/Program%20Files/Warez%20P2P%20Client/My%20Shared%20Folder/audi/Birthday%20Massacre%20-%20Happy%20Birthday.mp3, you might need to install the corresponding plugins ... as an example) what can i do to fix this?

---

### Post by KingBahamut on 2005-10-17
You need to install the gstreamer plugins 

sudo apt-get install gstreamer0.8-plugins 

That should give you all the stuff you need to play the proper media.

---

### Post by Ampersand on 2005-10-17
You'll have to get the gstreamer-mad plugin for mp3s. Follow these instructions to get the universe and multiverse repositories ([https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)), then install all the packages starting with 'GStreamer'. You should then be able to play mp3s. There's information about other formats here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats).

---

### Post by Llewxam on 2005-10-17
alright following that process right now. i'll post if anything happens. so far that's for mp3s... so i need the plugins for dvds and other video media (mpg, avi) etc... erm .. nvm just read >.> my bad.

---

### Post by Llewxam on 2005-10-17
perfect... it works now with mp3s. downloading the dvd codecs at the moment. now ... how do i use the mozilla plugin? for streaming media?

---

### Post by Llewxam on 2005-10-17
:( dangit... k i finally got home and tried a dvd. it didn't work. also tried an .avi file and it didn't work either... o.0 what am i missing here? anyone? please?

---

### Post by Llewxam on 2005-10-17
bump.... anyone? please? :cry: i noticed when i tried to install mplayer that i have conflicts with libc6. so i think i'll stick to totem. i've done everything i was told here and i get nothing.

---

