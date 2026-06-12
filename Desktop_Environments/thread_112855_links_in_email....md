---
title: "links in email..."
date: 2006-01-05
forum: Desktop Environments
---

### Post by unionjak on 2006-01-05
hello,
i am using breezy with kde and no matter what email app i use (thunderbird,evolution etc) i can not goto the web page provided by the links in the email. I am not sure what is going on, so i am a bit stuck...any idea`s ?
steve.

---

### Post by joe_d on 2006-01-05
Here's a link that helped me with this [FOR Thunderbird only]:

look at the 3rd entry:
[forums.mozillazine.org/viewtopic.php?t=296052&highlight=click+url+open+firefox](forums.mozillazine.org/viewtopic.php?t=296052&highlight=click+url+open+firefox)

in my user.js file my path was "/usr/lib/mozilla-thunderbird" (ie. that's where i put the 'openlink.sh' script.

My openlink.sh is slightly diff:

#!/bin/sh

export MOZILLA_FIVE_HOME="/usr/lib/mozilla-firefox"

url="$1"
if [ "x$url" = "x" ]; then
url="about:blank"
fi

if $MOZILLA_FIVE_HOME/mozilla-thunderbird-xremote-client openURL\("$url, new-tab"\); then
exit 0
fi
exec $MOZILLA_FIVE_HOME/firefox "$url"

---

### Post by MartinG on 2006-01-05
If you're using kde then kmail (the obvious choice of client IMHO?) is easily set up:
System settings->User account->Default applications->Web browser (enter the path to your choice of browser).

This *might* do the trick for Thunderbird or Evolution, but I fear not.  For Evolution you will probably need to delve into the configuration options for Gnome (which I have never found easy), while for Thunderbird there must be some sort of setting?

(EDIT) See joe_d re Thunderbird.

---

