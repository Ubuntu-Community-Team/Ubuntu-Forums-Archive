---
title: "Firefox Multiple HomePage Tabs"
date: 2016-02-09
forum: Desktop Environments
---

### Post by icsd08063 on 2016-02-09
Hello to everybody! My first question here and i am really hoping for an answer...
So, here is the problem. I use Ubuntu 12.04 Kiosk with Firefox 28 (do not ask why and how, it just works) and what i wanna do is pretty simple: set 2 tabs as homepage. Pipe character would be the solution for me but here is the tricky part. When i set in user.prefs file the two url's, firefox starts normally with 2 tabs open (so far so good) but when session is killed, firefox reopens with this link in address bar

```
[http://www.mozilla.org]("http://www.mozilla.org/")|[http://www.google.gr]("http://www.google.gr/")
```

For some reason that i still can not understand, it reads those 2 url's as one and it tries to open them - with no success of course. So what i wanna do is pretty simple: Ubuntu Kiosk running firefox with 2 tabs as home page, even when session is resetted after 1 minute (that's the threshold i have stated).
Any help???

update: I tried upgrading ff to latest version and problem still remains. So i guess it is definitely not an old version issue. Also i figured out that when ff starts for the first time after reboot, it reads the .xsession file and not the user.js file for the homepage. After ff resets, all things messed up... 

user.js file
```
user_pref("browser.startup.homepage", "[www.mozilla.org]("http://www.mozilla.org/")|[www.google.com]("http://www.google.com/")");
user_pref("browser.startup.homepage_override_url", "");
user_pref("browser.startup.homepage_welcome_url", "");
user_pref("browser.startup.homepage_override.mstone", "ignore");
user_pref("network.proxy.http", ""); 
user_pref("network.proxy.http_port", ); 
user_pref("network.proxy.no_proxies_on", "localhost, 127.0.0.1"); 
user_pref("network.proxy.share_proxy_settings", false);
user_pref("browser.cache.disk.enable", false); 
user_pref("browser.cache.memory.enable", false);
user_pref("browser.urlbar.autocomplete.enabled", false); 
user_pref("browser.urlbar.showPopup", false); 
user_pref("browser.urlbar.showSearch", false); 
user_pref("extensions.kioskreset.inactivity.seconds", 600);
user_pref("privacy.sanitize.promptOnSanitize", false); 
user_pref("privacy.sanitize.sanitizeOnShutdown", true); 
user_pref("network.cookie.enableForCurrentSessionOnly", true);
user_pref("network.protocol-handler.external.snews", false); 
user_pref("network.protocol-handler.external.news", false); 
user_pref("network.protocol-handler.external.irc", false); 
user_pref("network.protocol-handler.external.mail", false); 
user_pref("network.protocol-handler.external.mailto", false);
user_pref("accessibility.typeaheadfind.autostart", false); 
user_pref("privacy.clearOnShutdown.siteSettings", true); 
user_pref("browser.sessionstore.enabled", false); 
user_pref("browser.sessionstore.resume_from_crash", false); 
user_pref("browser.sessionstore.resume_session_once", true); 
user_pref("browser.sessionstore.interval", 100000);

```

---

### Post by papibe on 2016-02-09
Hi icsd08063. Welcome to the forum ):P

You could call the tabs as parameters instead of using internal settings. This should work:
```
firefox -new-tab -url 'www.mozilla.org' -new-tab -url 'www.google.com'
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by icsd08063 on 2016-02-09
> **papibe said:**
> Hi icsd08063. Welcome to the forum ):P

You could call the tabs as parameters instead of using internal settings. This should work:
```
firefox -new-tab -url 'www.mozilla.org' -new-tab -url 'www.google.com'
```
Hope it helps. Let us know how it goes.
Regards.

First of all, thank you for replying!
I'm gonna try it in a while and let you know!

Once again, thank you!

---

### Post by icsd08063 on 2016-02-09
Unfortunately, no success.

First of all, here is the .xsession file located in home directrory of user.

```

#!/usr/bin/env bash
xautolock -secure -time 15 -locker /usr/local/bin/kill_firefox.sh
metacity&
xscreensaver -no-splash &
firefox

```

_info:_ problem does not exists at all with only one ff tab, it only produces itself when the 2 tabs scenario comes ahead

Here is what i did:
I first changed the above code to what **papibe**[COLOR=#000000] suggested

[/COLOR]```

#!/usr/bin/env bash
xautolock -secure -time 15 -locker /usr/local/bin/kill_firefox.sh
metacity&
xscreensaver -no-splash &
firefox -new-tab -url 'www.mozilla.org' -new-tab -url 'www.google.com'

```[COLOR=#000000]

Then, i altered the user.js file and left blank the first row

[/COLOR]```
[COLOR=#000000]
user_pref("browser.startup.homepage"), "");
[/COLOR]
```

and deleted sessionstore.js, sessionstore.bak, prefs.js files

_Result:_ FF opened with two tabs after reboot but when session killed, it opened just a single empty tab (New tab, search or enter address)

I tried the above with no user.js file and it happened the same exactly.

Any ideas why this is happening???
My best thought is that for some reason, ff does not read the xseesion script when it loads again..

---

### Post by icsd08063 on 2016-02-12
Anyone???

---

### Post by icsd08063 on 2016-03-08
Good morning everybody,

So, i have found the problem generating the error.
One of my plugins, kioskfox, had a setting which could alter the homepage.
I simply disabled the addon as firefox could handle just fine both multuiple homepages and cookies / history.

So ,yes, kioskfox does not support multiple firefox homepages!
Thx, everyone for the help!

---

