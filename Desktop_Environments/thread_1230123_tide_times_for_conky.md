---
title: "tide times for conky"
date: 2009-08-03
forum: Desktop Environments
---

### Post by glennnf on 2009-08-03
Hi,just wondering if anybody has a script for tide information for conky.
Kaivalagi has one for just about everything else,any takers,Thanks,Glennnf.:D

---

### Post by lowsnr on 2010-02-20
I know this thread is a bit old, but if anyone else is searching for something similar, here's what I did:

First, install xtide and xtide-data - it generates tide predictions:
```

lowsnr@fulcrum ~ $ sudo apt-get install xtide xtide-data

```

Second, create a script to generate data and parse the results. Change the value of XTIDE_DEFAULT_LOCATION to whatever your local tide station is (mine is King Harbor, Redondo Beach, CA)
```

lowsnr@fulcrum ~ $ gedit conkyTide.sh

```
```

#!/bin/sh

export XTIDE_DEFAULT_LOCATION="King Harbor"
tide -f c 2>/dev/null | grep -i tide | head -n 1 | sed 's/ PST//' | awk -F, '{ print $3,"-",$5":",$4 }'

```
```

lowsnr@fulcrum ~ $ chmod +x conkyTide.sh

```

When run, this script will print something along the lines of '01:35 PM - High Tide: 2.36 ft'.  You can change the number of lines it displays by changing the 'head -n 1' command; mine is set for a single-line display of the next tide peak (high or low).  Also change 'PST' to your local time code if you want to get rid of it like I did.

Now you can add it to your Conky config like any other script.  Enjoy!

~ LowSNR

---

