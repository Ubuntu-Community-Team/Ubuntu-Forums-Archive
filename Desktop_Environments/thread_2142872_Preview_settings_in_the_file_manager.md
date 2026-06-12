---
title: "Preview settings in the file manager"
date: 2013-05-07
forum: Desktop Environments
---

### Post by minemax on 2013-05-07
When I set "Show thumbnails->Local Files Only" and "**Only for files smaller than**: ..." this last filter doesn't work -- previews are still shown for all files, no matter how big.
Is it a bug?

Ubuntu 13.04, 64 bit.

---

### Post by papibe on 2013-05-07
Hi minemax.

Previews refers to the creation of a thumbnail. If the thumbnail was created before, it'll be displayed.

Test previews for new pics by copying an existing (big) picture. The new file's thumbnail should not be created, and also not displayed.

Let us know how it goes.
Regards.

---

### Post by minemax on 2013-05-07
I don't think it's because of the thumbnail cache. Actually even the default settings were "local files only, smaller than 10 MB" and the preview works for all my videos, e.g.
> **papibe said:**
> Test previews for new pics by copying an existing  (big) picture. The new file's thumbnail should not be created, and also  not displayed.
Let us know how it goes.
Regards.
I tried it. Still the same situation.

---

### Post by papibe on 2013-05-07
I see.

I tested pictures, and it works. Does pictures previews work for you, as it should be?

Regards.

---

### Post by minemax on 2013-05-08
> **papibe said:**
> I see.

I tested pictures, and it works. Does pictures previews work for you, as it should be?

Regards.

Actually, it works for new pictures, yes. :eek:  So, it seems you were right and I was a little bit confused by the strange handling of video files by the Files manager. These are also files definitely, and should not be previewed if the option "Only for smaller than" is activated.
Why this is important. For example, I've downloaded several episodes of a tv show, let's say it is "Survivor", and I don't want any spoilers. :popcorn:


So, is it possible to turn the preview off just for the video files?

---

### Post by mc4man on 2013-05-09
> **minemax said:**
> 
So, is it possible to turn the preview off just for the video files?
In a typical Ubuntu install mv  /usr/bin/totem-video-thumbnailer to a .bak

```

sudo mv /usr/bin/totem-video-thumbnailer /usr/bin/totem-video-thumbnailer.bak
```
To turn back on reverse the  command
sudo mv /usr/bin/totem-video-thumbnailer.bak /usr/bin/totem-video-thumbnailer

Edit: you'd need to remove the .cache/thumbnails/normal folder to remove existing if desired

---

### Post by minemax on 2013-05-10
Ok, I've uninstalled Totem (VLC is much better), removed some thumbnail cache and now everything works fine. :) Thank you, guys.

---

