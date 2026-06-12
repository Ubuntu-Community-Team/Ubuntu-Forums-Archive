---
title: "Evolution Mail Address Cache"
date: 2008-05-07
forum: Desktop Environments
---

### Post by bensode on 2008-05-07
Ubuntu 8.04 64 bit edition with Evolution 2.22.1 using the Exchange connector.

Somehow a bad address has been cached into Evolution.  Even when I search from the addressbook and insert it, Evolution changes it to the bad cached name and address.  How can I clear the local cache of names & addresses when composing new messages?  Thanks!

---

### Post by Kobalt on 2008-05-07
Hello,

Have you tried to clear the /cache/addressbook folder in your hidden /.evolution folder? To access it go into your home folder and press Ctrl+H to see (or hide) hidden folders.

---

### Post by bensode on 2008-05-07
Do I need to close Evolution and stop it's daemons running before trying this?  Didn't think to look into the subfolders but sounds worth while to investigate just curious if everything for Evolution should be shutdown first or not.

---

### Post by Kobalt on 2008-05-07
Yes, I would do this manipulation with Evolution closed.

---

### Post by bensode on 2008-05-07
That did the trick with Evolution closed.  I navigated to ~/.evolution/cache/addressbook folder and deleted the folder entry that began with "gal__" for the Global Address List for Exchange.  I had to go into the Exchange addressbook and search for a name, after that it populated the cache again.  Thanks a bunch!

---

