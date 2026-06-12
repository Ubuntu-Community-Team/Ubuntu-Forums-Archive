---
title: "Solution for thunderbird mailto-problem"
date: 2005-01-27
forum: Desktop Environments
---

### Post by ember on 2005-01-27
Hi,

I had the same problem some users posted - mailto-links from firefox did only work, if thunderbird was not open. In other cases it opened the profile manager. Since I didn't find a working solution here, I managed write a small shell script (maybe it's not too elegant, because I don't do shellscripting very often, yet it works). It works with both clicking on mailto-links and the send link function in the file menu. 
Maybe this is of use for some people here.
```

#!/bin/bash
if mozilla-thunderbird -remote "ping()"; then
  url=`echo "$1" | sed -e's/^mailto://'`
  mozilla-thunderbird -remote "mailto($url)"
else
  mozilla-thunderbird $1;
fi

```

You'll have to set permissions to 755 and set the standard-gnome-handler to the location you placed the script in afterwards ("/usr/lib/mozilla-thunderbird/thunderbird.sh %s" in my case)

Best,
Ember

---

### Post by Georges on 2005-04-09
I have another solution, no script writing but script editing needed:

[http://ubuntuforums.org/showthread.php?p=123529#post123529](http://ubuntuforums.org/showthread.php?p=123529#post123529)

Georges

---

