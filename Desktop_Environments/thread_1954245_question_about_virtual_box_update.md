---
title: "question about virtual box update"
date: 2012-04-07
forum: Desktop Environments
---

### Post by forsubhi on 2012-04-07
can I update virtual box  without downloading the new package , I mean by sudo command

---

### Post by SeijiSensei on 2012-04-07
Follow the instructions at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) that concern "Debian-based distributions."  You'll need to add the "PPA" to your system as described there.  Then after "sudo apt-get update" followed by "sudo apt-get install virtualbox-4.1" you'll have the latest release from Oracle.

You might want to run "sudo apt-get purge virtualbox-*" first to remove any existing packages.

Don't forget to install the Guest Additions as well; again the virtualbox.org website will explain how to do this.

---

