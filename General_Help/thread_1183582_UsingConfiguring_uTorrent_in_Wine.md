---
title: "Using/Configuring uTorrent in Wine"
date: 2009-06-10
forum: General Help
---

### Post by Entropy_Sam on 2009-06-10
I'd like to use uTorrent in Wine, as IMO it's vastly superior to Transmission. I've seen Ubuntu users with uTorrent shortcuts on their desktop and I've successfully installed it, but I wasn't able to test the connection when I ran it. Are there any special steps I need to take in order to configure it?
 
How can I configure my browser to automatically open a .torrent file in uTorrent in Wine?
 
And finally, does anyone have successful experience of switching between different installations of uTorrent while continuing the same downloads? If both are configured to use the same directories, I should be able to continue downloads in Ubuntu which were started in XP, right?

---

### Post by Entropy_Sam on 2009-06-10
Well in case anyone else is wondering about this, I configured my browser to drop .torrent files in a specific directory, and configured uTorrent to automatically check that directory.

There were no network/port issues to resolve - it seems Wine has those bases covered well (if youre having issues with your router blocking downloads, you should try some networking forums).

Finally, I can resume downlaods in XP that were started in in Ubuntu and vice-versa - I just have to make suer they've both added the new torrent and each time one or the other starts up, it runs a check on what's been downloaded to catch up. Takes a few minutes, but now  can download the same torrents while I'm in either OS.

---

### Post by Fatman22 on 2009-06-10
I don't mean to Hijack, but I might say that I've got stupidly fast speeds using Transmission with TOR, although I did have forward a listening port past our linksys router, and change a Linksys setup to accept anonymous connections.  I also run the GUFW firewall application from Synaptic just incase I download something which tries to make an outbound connection.
 
BTW uTorrent in Wine works fine for me also, however it seems to crash every few hours if I am using TOR as a proxy for downloads via html.

---

### Post by Entropy_Sam on 2009-06-10
Not much of a thread to hihack ;-)

Well I'll probably avoid using proxies, then. I'm really just interested in being able to continue my download in more than one OS.

---

### Post by Hund on 2009-06-10
I would recomend Deluge. The GUI reminds of µTorrent. But imo it works better than µTorrent and it's open source. :)

---

### Post by mackerman on 2009-06-12
How does one configure Firefox to drop .torrent files in a specified directory, while leaving the default directory the Desktop?  Possible?

---

