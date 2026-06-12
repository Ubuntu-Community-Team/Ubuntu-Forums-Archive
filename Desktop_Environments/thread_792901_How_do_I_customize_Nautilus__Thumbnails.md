---
title: "How do I customize Nautilus / Thumbnails"
date: 2008-05-13
forum: Desktop Environments
---

### Post by tep200377 on 2008-05-13
I have a problem configuring Nautilus to show thumbnails in different ways. When the thumbnails are showing small icons, it enlarge the icons to a silly big size. 

See image below: [http://www.dump.no/files/4a6f7dd85ed5/Screenshot-icons_-_File_Browser.png](http://www.dump.no/files/4a6f7dd85ed5/Screenshot-icons_-_File_Browser.png)
[IMG]http://www.dump.no/files/4a6f7dd85ed5/Screenshot-icons_-_File_Browser.png[/IMG]

Is there a way to customize this thumb preview?

---

### Post by bmac on 2008-05-13
What happens when you hit the negative magnifying glass next to "view as icons"? Does it remember the reduced setting when you reopen Nautilus?

---

### Post by Awalton on 2008-05-14
> **tep200377 said:**
> I have a problem configuring Nautilus to show thumbnails in different ways. When the thumbnails are showing small icons, it enlarge the icons to a silly big size. 

See image below: [http://www.dump.no/files/4a6f7dd85ed5/Screenshot-icons_-_File_Browser.png](http://www.dump.no/files/4a6f7dd85ed5/Screenshot-icons_-_File_Browser.png)
[IMG]http://www.dump.no/files/4a6f7dd85ed5/Screenshot-icons_-_File_Browser.png[/IMG]

Is there a way to customize this thumb preview?

Yes, with a gconf key (/apps/nautilus/icon_view/thumbnail_size) but it won't help this particular issue. This is a bug in our thumbnailing code since 2.22, and it's a known issue. Normally, we don't thumbnail images below the thumbnail threshold, we just use the image itself.

---

