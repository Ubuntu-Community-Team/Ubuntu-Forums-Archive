---
title: "[SOLVED] Nautilus keeps reloading my thumbnails"
date: 2008-07-06
forum: Desktop Environments
---

### Post by Ekeluo on 2008-07-06
Okay. I have to say this must have been my fault: after trying to remove "orphaned" libraries with deborphan (gtkorphan gui) I manage to get nautilus epileptic about media thumbnails (meaning anything that generates thumbnails). It keeps reloading them after a random amount of time. This is rather frustrating as some of my folders have 40+ rmvb videos in them and I like o see their thumbnails. I tried reinstalling some ubuntu-desktop dependent libraries but no luck. Pls any help will be appreciated.

P.S. If this matters I think this has to do with what tells nautilus where the thumbnails are; AFAIK my ~/.thumbnails folder is fine and well populated.

---

### Post by Ekeluo on 2008-07-06
Help, Pleeeeeeease ](*,)

---

### Post by sayakb on 2008-07-07
Disable thumbnail display and enable it again from nautilus preferences. Make sure that thumbnails display is set to **Local Files Only **when you re-enable it.

---

### Post by Ekeluo on 2008-07-07
Oooooohh, thanks all fine now :), will stress the bugger to certify

---

### Post by Ekeluo on 2008-07-07
It seems to still do it. I noticed it certainly occurs after I open the menu (I use gnome-main-menu) and view recently used documents, where it shows thumbnails of recently played videos. I don't have to restart X or any thing do I?

---

### Post by Ekeluo on 2008-07-12
Someone pleeeeeeeze help me on dis... I've completely changed user (which solved my slow login issues :)) but this seems to go on. Happens every time I access the file (e.g for playback, etc). I have not idea what to do, really need help :(.

Please..

---

### Post by Ekeluo on 2008-07-17
bump

---

### Post by Ekeluo on 2008-07-18
Well after fiddling some more I finally fixed it. Turns out enabling system-wide recently used files (I did this via ubuntu tweak, maybe there should be a warning for this) list makes it do that. I think it has some thing to do with permissions on the thumbnail file after being accessed by root or different user. Hope this helps anyone there with this queer problem. 

P.S. Isn't this a bug of some sort?

---

