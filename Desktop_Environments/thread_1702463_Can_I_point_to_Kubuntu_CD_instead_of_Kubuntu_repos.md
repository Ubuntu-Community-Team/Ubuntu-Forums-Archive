---
title: "Can I point to Kubuntu CD instead of Kubuntu repository?"
date: 2011-03-07
forum: Desktop Environments
---

### Post by deepaknet on 2011-03-07
Dear Kubuntu Team,

I would like to apply KDE on my Kubuntu because the current one blew up. But each time I to sudo get-apt it seems to be fetching from the cloud. Is there a way I can make it to read from my local Kubuntu CD? I have both Ubuntu 10.04 LTS and Kubuntu Live CDs.

I believe the local disk read should be faster to translate than to bite the bytes across thousands of miles over the wire right?

---

### Post by Krytarik on 2011-03-07
I don't know where you find those options in KDE, but in Gnome you can select the sources via "System -> Administration -> Software Sources". And you can also open the same dialog via "Settings -> Repositories" in Synaptic. After you selected the CD instead of the internet sources you have to update apt.

---

