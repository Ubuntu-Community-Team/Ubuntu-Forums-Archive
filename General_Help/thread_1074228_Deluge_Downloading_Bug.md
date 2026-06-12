---
title: "Deluge Downloading Bug?"
date: 2009-02-19
forum: General Help
---

### Post by konqueror7 on 2009-02-19
sorry if i posted it here...

i just noticed that deluge is still continuing to download even if i paused the download, is it normal or a bug. i mean, its called 'Pause' meaning to temporarily stop, and why is deluge still downloading?:)

---

### Post by mb_webguy on 2009-02-19
Does it do this for an extended period of time, or just for a minute or two after you click the button?

If it's the latter, this is normal.  A torrent file is divided into pieces of a certain size which varies from torrent to torrent.  For example, I'm currently downloading two videos, one which is divided into 185 2MB pieces, and the other which is divided into 701 512KB pieces.  Deluge (and most other torrent clients) won't stop the download of a piece in order to avoid data corruption.  It will wait until the pieces currently being downloaded are done first.

Therefore, if I click to Pause the download of the video with 2MB pieces, it will likely take a bit longer to actually stop than if I clicked to Pause the one with the 512KB pieces, because it may need to finish downloading potentially four times as much data before it gets to a good place to stop.

---

### Post by konqueror7 on 2009-02-19
nope, it still went to download continuously, i think its eating around 20kb...i paused it on 10%, then when i return, it was 19% and so on...maybe it is really a bug?

---

### Post by Mercury_Alpha on 2009-02-19
Which version are you using? The one in the repos is pretty old, unfortunately.

---

### Post by mb_webguy on 2009-02-19
Possibly.  What version of Deluge are you using?  The one in the official repos, or the most recent?

If you're using the repo version, try updating to the newest version either by downloading the deb from the Deluge website, or by adding the [Deluge PPA]("https://launchpad.net/~deluge-team/+archive/ppa") to your software sources.

---

### Post by konqueror7 on 2009-02-19
version 0.5.9.3, i downloaded it through ubuntu tweak...i don't really care if its still downloading, i just want to clarify if its a bug or not?:o

---

### Post by Mercury_Alpha on 2009-02-19
It sounds like a bug. The current version is 1.1.3, which you can grab [from their PPA]("https://launchpad.net/~deluge-team/+archive/ppa").

---

### Post by konqueror7 on 2009-02-19
i better upgrade this...thanks to all your opinions!

---

### Post by konqueror7 on 2009-02-19
upgraded it, still the same...paused my torrent at 85%, surprised me that it suddenly that it was finished downloading...:D

---

