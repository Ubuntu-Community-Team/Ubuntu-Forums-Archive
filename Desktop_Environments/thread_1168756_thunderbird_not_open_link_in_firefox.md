---
title: "thunderbird not open link in firefox"
date: 2009-05-24
forum: Desktop Environments
---

### Post by parsibox on 2009-05-24
hi
i install thunderbird from source 
when i click in links in email my openlink.sh luanch but firefox not start.

this is my openlink.sh source :
```

#!/bin/bash

url="$1"
if [ "x$url" = "x" ]; then
url="about:blank"
fi

exec /usr/bin/firefox "$url"

```

i think openlink.sh not work or nut call but i test all
i user terminall to launch openlink.sh and it work and open firefox.

what can i do to fix this problem?

---

