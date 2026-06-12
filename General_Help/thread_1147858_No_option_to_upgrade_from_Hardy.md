---
title: "No option to upgrade from Hardy"
date: 2009-05-03
forum: General Help
---

### Post by MikeBenza on 2009-05-03
I want to upgrade from Hardy to Intrepid and Intrepid to Jaunty.  I go to the update manager and I click "Check," but the option to upgrade isn't shown.

If I run "sudo update-manager -c", the option to upgrade isn't shown.

If I run "sudo do-release-upgrade", it says "Checking for a new ubuntu release" then "No new release found"

I'm running Hardy with all the updates installed on a 64 bit machine.  Here's my uname -a:
Linux mikebenza-dell 2.6.24-23-generic #1 SMP Wed Apr 1 21:43:24 UTC 2009 x86_64 GNU/Linux

My software sources server is set to the main server.

Any ideas how to actually upgrade?

---

### Post by hexanol on 2009-05-03
It's normal, since Hardy is a long term release.

To solve your problem, go to System -> Software Sources. Under the tab "Updates", at the bottom, you'll find what you are looking for.

---

### Post by UbuntuNerd on 2009-05-03
go to your software sources and under the update tab at the bottom where it says Release Upgrade set it to: normal releases then check for updates

---

### Post by MikeBenza on 2009-05-03
Thanks

---

