---
title: "Open links in firefox from thunderbird"
date: 2008-04-28
forum: Desktop Environments
---

### Post by AlainJLEB on 2008-04-28
Hey there,

In 7.10, thunderbird was able to directly open http links into the running firefox in a new tab ... since the upgrade to 8.04, it's no more working ... where can I set this up? I've searched the preference of thunderbird without finding this ... 

In the other direction, how can I tell firefox to use thunderbird to handle mailto: links?

Alain

---

### Post by chandra on 2008-04-28
Clicking on a mailto link in Firefox 3.0b5 does not seem to open a Thunderbird compose window either. See this discussion:

[http://ubuntuforums.org/showthread.php?t=771218&highlight=Thunderbird+mailto+Firefox](http://ubuntuforums.org/showthread.php?t=771218&highlight=Thunderbird+mailto+Firefox)

and also this Launchpad bug report:

[https://bugs.launchpad.net/bugs/222944](https://bugs.launchpad.net/bugs/222944)

---

### Post by AlainJLEB on 2008-04-28
> **AlainJLEB said:**
> In the other direction, how can I tell firefox to use thunderbird to handle mailto: links?

This is solved by updating Firefox configuration:
-) about:config
-) double-click on network.protocol-handler.app.mailto
-) ensure it is /usr/bin/thunderbird and not something else like mozilla-thunderbird

Now, the question still remainds: how to allow thunderbird to open URL in firefox?

---

### Post by xjb2003x on 2008-04-28
I had the same problem, but without being at home it is hard for me to answer that.  I can tell you that I was able to find the solution after searching the forums.

---

### Post by rjmoerland on 2008-04-28
> 
Now, the question still remainds: how to allow thunderbird to open URL in firefox?

Perhaps this is what you're looking for: [click]("http://justanothertechblog.blogspot.com/2006/07/thunderbird-configured-to-open-links.html")

Just as a sidenote, after updating my Xubuntu from 7.10 to 8.04, I lost all the clickable links throughout the desktop environment. It's as if there's no default browser set, though the 'preferred applications' dialog says it is. Do you have the same problem?

---

### Post by AlainJLEB on 2008-04-29
> **rjmoerland said:**
> Perhaps this is what you're looking for: [click]("http://justanothertechblog.blogspot.com/2006/07/thunderbird-configured-to-open-links.html")


Indeed, that's what I was looking for. Thanks :)

To summarize all of this, you need to ensure that the protocol handlers are pointing to the correct program. In both thunderbird and firefox, the settings were referring to something like /usr/lib/firefox-bin or /usr/bin/mozilla-thunderbird, where it is expected to have /usr/bin/firefox and /usr/bin/thunderbird. 

Those parameters are 
[LIST]
[*]in thunderbird:
[LIST]
[*]network.protocol-handler.app.http
[*]   network.protocol-handler.app.https
[/LIST]
[*]in firefox:
[LIST]
[*]network.protocol-handler.app.mailto
[/LIST]
[/LIST]

---

### Post by chandra on 2008-05-02
> **AlainJLEB said:**
> This is solved by updating Firefox configuration:
-) about:config
-) double-click on network.protocol-handler.app.mailto
-) ensure it is /usr/bin/thunderbird and not something else like mozilla-thunderbird...

In FF 3.0b5, even with the above set, mailto: links do not open up a Thunderbird compose window.

Hence the bug report.

---

### Post by chandra on 2008-05-13
See

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222944](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222944)

for a workaround to the Firefox 3.0b5-Thunderbird mailto problem.

---

