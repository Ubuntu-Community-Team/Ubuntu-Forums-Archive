---
title: "Continuing Download session in vuze that was started on windows"
date: 2009-05-05
forum: General Help
---

### Post by McTricks on 2009-05-05
I just saw that Vuze has a linux version, and I was wondering if it is possible to continue downloading the torrent I've been downloading in windows.. from Ubuntu...

In case that was confusing... example:

I'm in windows, downloading a torrent, and I decide to boot over into Ubuntu, and I can load up Vuze there, and keep on downloading the same torrent.

Is that possible?

EDIT:

And mabye vise-versa

---

### Post by lovinglinux on 2009-05-05
Yes, it's possible, but I never tried.

You have to configure the clients on both OSs to use the same folder for saving the downloaded contents (not the .torrent file) and it must be on a NTFS partition, so Windows can see it ( Ubuntu can see NTFS partitions, but Windows cannot see ext3 or ext4 partitions out-of-the-box ).

Then when you launch the .torrent file for a content that you have already started downloading on the other OS, you must select the option "recheck", so the client can compare the content described in the .torrent file with the content itself. It will then determine the amount of data already downloaded and start from where you stopped.

You don't necessarily need to use the same client (Vuze) on both machines, since the torrent protocol is the same for every client and they will all recheck the downloaded file.

Have you tried Deluge? It is much less CPU hungry than Vuze, it is simple to configure, has several important features and also have versions for Windows and Ubuntu. Most important, it is open source.

---

### Post by McTricks on 2009-05-05
OK, thanks, that seems to be working :)

---

