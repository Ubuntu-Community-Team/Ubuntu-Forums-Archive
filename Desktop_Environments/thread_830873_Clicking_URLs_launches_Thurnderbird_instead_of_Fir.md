---
title: "Clicking URLs launches Thurnderbird instead of Firefox"
date: 2008-06-16
forum: Desktop Environments
---

### Post by potatan on 2008-06-16
Hi,

Problem with a friend's laptop - whenever she clicks a URL on the desktop, Thunderbird loads up instead of Firefox 2.  This has only started happening recently.  

The system is Hardy Heron with Firefox 3 uninstalled and replaced with version 2 (she didn't like the beta).

I have checked System/Prefs/Preferred Applications, and URLs are set to "Custom" with "firefox-2 %s" as the launch command.

I have also checked Firefox preferences and it is set as the default browser.

I have tried marking Firefox 2 for reinstallation.

But it still loads Thunderbird when I click a desktop link.

Any ideas?

I'm sure I've had this problem myself a long time ago, but can't remember what I did to fix it - and google searches seem to just bring back problems launching links from within Thunderbird emails, which is not the same problem at all.

Many thanks in advance.

p.s. I don't have access to the laptop here, but they only live round the corner from me.

---

### Post by Zorael on 2008-06-16
Not ever having had this problem you're describing, the only thing I can think of is to make sure the xdg alternative is set to Firefox.
```
$ sudo update-alternatives --config x-www-browser
```
Failing that, I'd try uninstalling Thunderbird. Perhaps removing it fixes whatever is pointing to it to point to Firefox instead. Then reinstall and hope the setting sticks.

---

### Post by potatan on 2008-06-17
Thanks, I'll give your suggestions a try later.

If there first one doesn't work, is there a way of uninstalling/reinstalling Thunderbird without losing all the profile information, contacts, settings etc.?

Thanks

---

