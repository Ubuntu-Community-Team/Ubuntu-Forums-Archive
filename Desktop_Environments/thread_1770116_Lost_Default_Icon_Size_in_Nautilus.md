---
title: "Lost Default Icon Size in Nautilus"
date: 2011-05-28
forum: Desktop Environments
---

### Post by stevedude on 2011-05-28
Hello,

For some reason I lost my default icon sizes in Nautilus. This only appears to affect any graphic files like .jpg, .png, etc. that I keep in my "Pictures" folder. I also have this issue with video files that I keep in my "Video" folder.

Currently I am running Ubuntu Natty and using the Ambiance theme that is customized with Faenza Mint icons. Nautilus is customized with Nautilus Elementary. Changing themes has no effect. The folders all appear normal and other icon file types appear normal, it's just my graphic and video files that are appearing small.

Running dconf editor shows my icon setting is set to normal. I am enclosing a pic so you can see the folders display at a normal size, but the graphic files do not. Any assistance is appreciated.

---

### Post by Krytarik on 2011-05-28
I just figured that the size of thumbnails in Nautilus is set by the Gconf key "/apps/nautilus/icon_view/thumbnail_size". By default it's set to "96", it seems like it's set to a much lower value at your system. You can check/modify it with "gconf-editor".

Greetings.

---

### Post by stevedude on 2011-05-28
Thanks Krytarik for the reply,

I changed the icon_view value for thumbnail_size to 96. It was defaulting to 16.

That did the trick. Thank you for your assistance!

---

