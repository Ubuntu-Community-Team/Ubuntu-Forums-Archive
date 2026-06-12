---
title: "??Rename an MTP device??"
date: 2009-05-04
forum: General Help
---

### Post by LubindaMaim on 2009-05-04
My strange problem is the my 4gb sansa fuze where when i connect it under mtp mode, it mounts both the built in storage and the sd card under the same name it was fine when i looked at its info it said i had 9.5 gb storage (6gb card) but it only sends files to the 4gb device thought when full it should start putting stuff into the card but it didn't realized that they must still be separate but cose they have the same name media players somehow think its one device. The reason I 'need' to use mtp mode is i found banshee could sync artwork and podcasts perfectly as well as put working playlists on the device which in msc mode it doesn't do. hence i need a way to make the sd mount as a different mtp device.

---

### Post by mikezila on 2009-05-20
That's the way MTP mode works.  It combines the two storage locations as one single device.  That's the whole point of MTP mode.  It not adding to the sd when the built-in is full is likely a bug in libmtp.

If you want to use it as two distinct storage devices, you need to use MSC mode.

---

