---
title: "Looking for Good Way to sync local music to mp3 player"
date: 2006-01-05
forum: General Help
---

### Post by jabster on 2006-01-05
Hi.

I have a moderate sized mp3/ogg/flac collection, as well as a 20G iriver mp3 player.

I am still in the process of ripping some CDs, and purchasing music online, so I am more or less in constant need of syncing my iriver to what is on my hard drive.

Is there a good app to do this?

What I'm looking for is something that will scan my local HD and the iriver, copy (well, sync) over all mp3's and ogg's, as well as oggenc my flac's and move those over to the iriver.

Anybody got an app like that? Anybody willing to write one for me? :-) I'd prefer a KDE app obviously. soundKonverter isn't doing it for me (keep getting file not found errors on the flacs).

Right now, all I can think of is something like "rsync mp3,ogg"  to sync up the oggs & mp3s. Then "find localHD -flac -exec oggenc" (and probably output list to a file), then "rsync --from-file" those files to the iriver, deleting the oggs once rsync is done. Which I could do myself.

But I'd like a gui for this. Easier for me. And more importantly, easier for wife. My wife only has a 1G player, hence I'm also looking for a soundKonverter-like app.

Thanks,
john

---

