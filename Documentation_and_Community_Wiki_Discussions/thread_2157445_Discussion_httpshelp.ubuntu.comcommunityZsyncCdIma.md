---
title: "Discussion: https://help.ubuntu.com/community/ZsyncCdImage"
date: 2013-06-25
forum: Documentation and Community Wiki Discussions
---

### Post by FiremanEd on 2013-06-25
The Zsync information on [https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage) is showing information for the build: raring.  An update to saucy would better be suited.
> Updating the ISO

Ubuntu archives provide .zsync files using quite similar URIs about the various flavours. For example:

zsync [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync)

will sync the server's daily unstable raring (13.04) desktop image (for i386) to your local system with an older desktop image already stored on your hard drive.

Note 1: If you are using other flavours of Ubuntu don't forget to add the flavour's name in the zsync path after cdimage/, e.g.

zsync [http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-i386.iso.zsync)

zsync [http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-i386.iso.zsync)

Note 2: If you are using another architecture don't forget to change i386 in the zsync path with the correct architecture name, e.g.

zsync [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync)

---

### Post by bapoumba on 2013-08-04
Thread approved and closed as the wiki page has already been edited accordingly. Sorry your thread has probably gone overlooked due to the recent downtimes.

---

