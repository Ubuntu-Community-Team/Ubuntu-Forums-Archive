---
title: "Default application settings fail to operate in KDE"
date: 2008-01-09
forum: Desktop Environments
---

### Post by nadrach on 2008-01-09
If I click on a URL in Thunderbird, it does not open Firefox for the web page (actually, nothing happens) and if I click on a mailto: in Firefox, it does not open Thunderbird to write a message (nothing happens, again). After a discussion in my local LUG, this week, I have checked and confirmed the set up for the default applications in KDE to be Firefox (browser) and Thunderbird (email). Still nothing happens if I click on a URL in TB or a mailto: in FF.
Any suggestions as to what configuration I may have missed?

---

### Post by p_quarles on 2008-01-09
This is due to the following bug:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/52670](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/52670)

There's a (relatively) easy fix for this. In Firefox, you'll need to open up the configuration page by typing about:config in the address bar. Right click anywhere, and select "add string."

The name should be: network.protocol-handler.app.mailto
The value should be: thunderbird

Same basic thing for Thunderbird. Pull up the config page by going to Preferences >> Advanced, and select "Config Editor." For this one, you'll need to add two strings:
network.protocol-handler.app.http
and
network.protocol-handler.app.https

The value for both should be "firefox."

---

### Post by nadrach on 2008-01-13
Thank you, problem fixed. The only downside is that each new entry has "user" status, not system, so the edits have to be done separately for each user on a system.
As this has been around since 2005, is there any news on when it will be fixed? I ask, because the first feedback I had was "well it works fine in windows!", and I had no answer.

---

### Post by nadrach on 2008-05-06
With Hardy Heron, the fix to select "mailto" to go to Thunderbird, no longer works in Firefox 3b5. FF ignores the manual entry for a "network.protocol-handler" and still throws up a select screen, which for some reason on my system, wants to talk to Yahoo mail. When you use the select screen to search for TBird and set it as a default application, Firefox stores the configuration, then returns a message that this can be altered in the Preferences menu ... no it can't. There is no configuration entry for a default "mailto" setting in that menu, either in FF 3b5 or any previous version of FF that I have used.

What is going on?

---

