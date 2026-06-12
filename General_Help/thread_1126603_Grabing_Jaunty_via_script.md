---
title: "Grabing Jaunty via script"
date: 2009-04-15
forum: General Help
---

### Post by imbjr on 2009-04-15
Currently, on release day, I use the following script to grab the next 'buntu release as reasonably fast as possible:

```
#!/bin/sh

DOWNLOADED="N"
while [ $DOWNLOADED = "N" ]
do
	if 
		wget <location of Jaunty>.torrent
	then
		DOWNLOADED="Y"
	else
		DOWNLOADED="N"
		sleep 900
	fi
done

deluge <Jaunty torrent>.torrent
```

But it would be nice to have knowledge of when the BitTorrent client is done downloading and has started seeding, so I can Twitter that event.

rtorrent looks like the way to go, but it is not obvious how to control it. It may be possible to terminate the program when it is done, but I see no examples of ppl having done that. Hopefully, once the download is done, the Bash script would continue, so that the 2nd Twitter would be sent.

---

