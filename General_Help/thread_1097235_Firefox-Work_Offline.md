---
title: "Firefox-Work Offline"
date: 2009-03-15
forum: General Help
---

### Post by Tteddo on 2009-03-15
I am setting up an older computer for a customer who only has dialup. I am using Gnome-ppp to connect, which works fine, but when I launch Firefox it always comes up in "Work-Offline" mode no matter what I do. Anyone have any ideas? I tried setting it in About:config, but it reverts.

---

### Post by Bartender on 2009-03-16
I tried this fix in Ubuntu 8.10 and it seems to have worked:

[I]type "about:config" in your Firefox address bar, you will see a bunch of
configuration parameters, use the filter to reach the one named
"toolkit.networkmanager.disable" and set it to "true": from now on there
will be no interaction between Firefox and the network manager. Actually
I agree with you that this dependency is quite strange...
Hope this may help you.[/I]


Here's the link to the discussion
[http://www.nabble.com/Firefox-3:-how-to-avoid-offline-mode-startup---td17058203.html](http://www.nabble.com/Firefox-3:-how-to-avoid-offline-mode-startup---td17058203.html)

I tried closing FF several times and restarting; the setting hasn't reverted.

---

### Post by Tteddo on 2009-03-16
> **Bartender said:**
> I tried this fix in Ubuntu 8.10 and it seems to have worked:

[I]type "about:config" in your Firefox address bar, you will see a bunch of
configuration parameters, use the filter to reach the one named
"toolkit.networkmanager.disable" and set it to "true": from now on there
will be no interaction between Firefox and the network manager. Actually
I agree with you that this dependency is quite strange...
Hope this may help you.[/I]


Here's the link to the discussion
[http://www.nabble.com/Firefox-3:-how-to-avoid-offline-mode-startup---td17058203.html](http://www.nabble.com/Firefox-3:-how-to-avoid-offline-mode-startup---td17058203.html)

I tried closing FF several times and restarting; the setting hasn't reverted.

That worked perfectly! Thanks!

---

