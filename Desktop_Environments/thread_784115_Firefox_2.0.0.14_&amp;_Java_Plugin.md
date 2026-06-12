---
title: "Firefox 2.0.0.14 &amp; Java Plugin"
date: 2008-05-06
forum: Desktop Environments
---

### Post by schnarff on 2008-05-06
My situation is slightly off from everything else I'm seeing on the forums here and on the web, so hopefully I'm not duplicating effort asking this question.

I've got Ubuntu 6.06-LTS running on an AMD64 box. For some time, I've had Firefox 1.5 running with the Blackdown Java plugin (1.4.2, to be specific); it's worked like a charm.

I just installed Firefox 2.0.0.14 by downloading it from mozilla.com and then placing it in /usr/local/firefox (plus a symlink to make /usr/local/bin/firefox work). After seeing that the Flash plugin finally worked, I was ecstatic, and went to go open a Java applet. I ended up with the manual install prompt, and after some digging, found that only the Blackdown Java plugin -- not the Sun version -- worked on AMD64.

After a bit more digging, I found several articles that suggested that, so long as ~/.mozilla/plugins/libjavaplugin_oji.so and /usr/local/firefox/plugins/libjavaplugin_oji.so were both symlinks to /usr/local/j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so (which is where /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so -- my 1.5 installation -- points), I should have no trouble running the plugin.

The problem is, I've created both of those symlinks, and not only do Java applets not run in the browser, I'm not even seeing Java in about : plugins. Does anyone have any idea what I'm doing wrong?

---

