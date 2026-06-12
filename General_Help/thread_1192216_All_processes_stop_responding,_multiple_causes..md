---
title: "All processes stop responding, multiple causes."
date: 2009-06-19
forum: General Help
---

### Post by Toadinator on 2009-06-19
Okay, so I have a huge problem. Ubuntu's been working like a charm ever since I installed it, but as soon as I upgraded to the 9.04 beta, things have been really unstable... even now, with the latest updates. When I try some things, ubuntu totally freezes up. No programs will open, no windows will close or appear, and I can't log out/restart X (with that one keyboard command; yes, I enabled it). Here's some of the things that lead to this:

Closing Songbird (All versions, from fta's repository AND getdeb.net)

Closing Firefox/Shiretoko (This only sometimes happens. Regular Firefox from the ubuntu repos freezes ubuntu, but Shiretoko [3.5] from fta's repository on launchpad closes just fine, usually; if it does freeze everything, then an update usually fixes it. Currently, it's just fine)

Starting Frostwire (All versions)

Logging out and *sometimes* shutting down

Can anyone tell me how to find a solution to the problem? If there's no hope, then I'll just re-install later... Thanks!

---

### Post by Toadinator on 2009-06-19
bump... maybe I should just re-install.

---

### Post by cariboo on 2009-06-20
Did you follow these steps before upgrading?

[list]
[*] disable all ppa's and third party repositories
[*] make sure your previous version is fully up-to-date
[/list]

One other thing to make sure of, it to make sure the update finished. In a terminal type:

```
sudo apt-get -f install
```

this will install any missing packages and dependencies, then in the same terminal type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

the above comands should complete the upgrade is it didn't.

---

