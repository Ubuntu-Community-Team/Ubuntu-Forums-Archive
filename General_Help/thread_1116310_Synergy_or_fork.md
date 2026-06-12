---
title: "Synergy or fork?"
date: 2009-04-04
forum: General Help
---

### Post by street spirit on 2009-04-04
I use [Synergy]("http://synergy2.sourceforge.net/") every day; it's such a amazingly useful tool that I wouldn't know what to do without it. The problem is that for all practical purposes the project has been abandoned. The last release was three years ago, and since that time, the main (only?) developer has been tinkering with a 2.0 version, a complete rewrite of the package. In the Sourceforge forums, he [said]("http://sourceforge.net/forum/message.php?msg_id=4689824") he didn't have the time to support the 1.x releases, he'd rather focus on the new version, but he can't seem to find the time.

In the meantime, with every new development on desktops, more things are breaking, and the bugs are piling up. In Intrepid, Synergy has become next to unusable for KDE and Gnome users, unless they deactivate their desktop environment's clipboard tool (and they have to hunt the forums and [bug trackers]("https://bugs.kde.org/show_bug.cgi?id=182844") until they find this nugget of information). If I'm lucky, I can run a synergys server for an hour or two, and then it crashes.

```
Apr  1 21:21:31 babylon kernel: [ 9503.590366] synergys[7770]: segfault at c ip b7dbdd06 sp bf8a3714 error 4 in libstdc++.so.6.0.10[b7d60000+e3000]
Apr  2 10:43:56 babylon kernel: [43445.701074] synergys[6532]: segfault at c ip b7d3fd06 sp bfa26534 error 4 in libstdc++.so.6.0.10[b7ce2000+e3000]
Apr  2 20:25:54 babylon kernel: [78363.200900] synergys[30197]: segfault at c ip b7d1cd06 sp bfa01fb4 error 4 in libstdc++.so.6.0.10[b7cbf000+e3000]
Apr  3 17:40:41 babylon kernel: [ 7130.450440] synergys[6434]: segfault at c ip b7e9dd06 sp bfd83b24 error 4 in libstdc++.so.6.0.10[b7e40000+e3000]
Apr  3 18:29:41 babylon kernel: [10069.787193] synergys[16884]: segfault at c ip b7d78d06 sp bfc5e214 error 4 in libstdc++.so.6.0.10[b7d1b000+e3000]
Apr  3 21:36:30 babylon kernel: [21278.893374] synergys[21307]: segfault at c ip b7e98d06 sp bfd7e334 error 4 in libstdc++.so.6.0.10[b7e3b000+e3000]
Apr  3 22:17:04 babylon kernel: [23712.971115] synergys[3171]: segfault at c ip b7d65d06 sp bf94d6e4 error 4 in libstdc++.so.6.0.10[b7d08000+e3000]
Apr  3 22:53:50 babylon kernel: [25918.920701] synergys[5988]: segfault at c ip b7da0d06 sp bfc88a24 error 4 in libstdc++.so.6.0.10[b7d43000+e3000]
Apr  3 23:28:06 babylon kernel: [27975.583560] synergys[8496]: segfault at c ip b7d1ad06 sp bfa01f94 error 4 in libstdc++.so.6.0.10[b7cbd000+e3000]
Apr  3 23:28:51 babylon kernel: [28020.527806] synergys[10837]: segfault at c ip b7dadd06 sp bff93d24 error 4 in libstdc++.so.6.0.10[b7d50000+e3000]
Apr  3 23:29:14 babylon kernel: [28043.561028] synergys[10873]: segfault at c ip b7e82d06 sp bfe6ac04 error 4 in libstdc++.so.6.0.10[b7e25000+e3000]
Apr  3 23:30:21 babylon kernel: [28110.105004] synergys[10928]: segfault at c ip b7e50d06 sp bf837dd4 error 4 in libstdc++.so.6.0.10[b7df3000+e3000]
Apr  4 14:18:47 babylon kernel: [81416.378459] synergys[10973]: segfault at c ip b7dc5d06 sp bf9acf44 error 4 in libstdc++.so.6.0.10[b7d68000+e3000]
Apr  4 16:49:53 babylon kernel: [90482.174812] synergys[11750]: segfault at c ip b7d8ed06 sp bfb75254 error 4 in libstdc++.so.6.0.10[b7d31000+e3000]
Apr  4 17:26:36 babylon kernel: [92684.996935] synergys[24011]: segfault at c ip b7ef4d06 sp bfcda494 error 4 in libstdc++.so.6.0.10[b7e97000+e3000]
```

The Fedora maintainers [appear to have a patch]("https://bugzilla.redhat.com/show_bug.cgi?id=434539") for this specific problem, but the comments on their bugtracker basically confirm that the Synergy project is dead or in a coma. While it would be really helpful if that patch would make it into the Ubuntu repository in the future, I'm wondering if it wouldn't be less painful in the long run to switch to [one of the forks]("http://code.google.com/p/synergy-plus/wiki/OtherForks") that have appeared due to the project's inactivity.

Synergy-Plus looks like a good candidate, but I haven't tested it yet. Have any of you tried Synergy-Plus or one of the other forks? 

I can live without my clipboard manager, but I really don't want to go back to having 2-4 keyboards and mice on my desk ;).

---

### Post by nbolton on 2009-08-20
I'm always happy to see a fellow Synergist! :)

The [Synergy+]("http://code.google.com/p/synergy-plus/") project is basically picking up where Chris left off about 3 years ago. You may be interested to have a glance at the [list of fixed bugs]("http://code.google.com/p/synergy-plus/issues/list?can=1&q=status:ReallyFixed,MaybeFixed"), but if you look at the main issue list, there's more reported bugs there (from the original Synergy) then you could shake a stick at... Not sure if the segfault issue you mentioned has been fixed (I've never come across the problem myself), and I'm not sure if it's even been reported (doesn't ring any bells mind).

Anyway, I hope you find that helpful... Feel free to [follow me]("http://twitter.com/NickBoltonUK") on Twitter for dev updates (NickBoltonUK), or you can reach me on IRC (#synergy-plus on freenode.net).

---

