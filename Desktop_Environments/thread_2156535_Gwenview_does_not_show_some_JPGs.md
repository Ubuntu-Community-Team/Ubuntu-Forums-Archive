---
title: "Gwenview does not show some JPGs"
date: 2013-06-22
forum: Desktop Environments
---

### Post by dargaud on 2013-06-22
Hello all,
strange problem with Gwenview: I have some JPG files, always the same, which don't open in Gwenview if I double-click them in Dolphin. Gwenview just shows a gray background. But if I open the previous image in alphabetical order and go to the next one from within Gwenview, it displays fine. I checked with 'file' and IM's 'identify' and there's no difference that I can tell between the files.

Is there some kind of cache somewhere, maybe corrupted ?
THanks

---

### Post by SeijiSensei on 2013-06-22
Dolphin caches thumbnails in ~/.thumbnails, but it doesn't cache whole images as far as I know.

If I'm browsing a directory full of image files, I just open the directory itself with Gwenview and browse from there.  Right-click the directory name in Dolphin and pick Open With > Gwenview.  If that option isn't offered, choose "Other" and point to Gwenview.  You can later make that the first option in the list by using System Settings > File Associations and choosing an image mimetype like image/jpeg.

---

