---
title: "does ubuntu update version iso after release day?"
date: 2008-12-11
forum: General Help
---

### Post by sdowney717 on 2008-12-11
meaning when they officially release a new version, do future fixed bugs and file changes get incorporated into the current available download version?
Typically I redownload iso installs but if they dont change then why bother getting a new copy.

---

### Post by howefield on 2008-12-11
I don't think they do, unless it is a point revision and you'll see it in the version number, like 8.04.1 came after 8.04.

---

### Post by aaaantoine on 2008-12-11
As far as I know, this is only done for LTS releases such as 8.04 (Hardy).  Three months after Hardy was released, Canonical put together several patches and updated the ISO images, bringing the version up to 8.04.1.

It is only when you see that .1 or .2 at the end that you can conclude that the image was updated.  It would be a bit dangerous to release a new ISO image without bumping the version number somehow.

If the ISO file has the same name, it should be the exact same image.

---

### Post by Rocket2DMn on 2008-12-11
Moved to General Help

The posters above are correct, dot extensions on the version or similar to service packs, and new .iso files are uploaded.  It would take too much time to package and test a new image every time updates are released, and documentation would have to be updated.

New images (called a daily build) are released each day for Ubuntu's development release, but this is a testing version and is not for regular home users.  Development images are constantly changed with many updates released every day, so it is more viable to do this for the development version, esp. since it doesn't undergo strict testing or documentation procedures like a stable release image does.

---

