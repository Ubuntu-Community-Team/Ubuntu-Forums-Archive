---
title: "How exactly might I start SABnzbd+, or anything else, as a service?"
date: 2009-01-09
forum: General Help
---

### Post by wracktail on 2009-01-09
I installed the program from JCF Ploemen's repository (located at [http://ppa.launchpad.net/jcfp/ubuntu/](http://ppa.launchpad.net/jcfp/ubuntu/)), and I've been trying to make sure that the program is configured properly and in such a way that someone who might be, well, less than computer literate can use it.

At the bottom of SABnzbd+'s wiki page for the aforementioned repository ([http://sabnzbd.wikidot.com/install-ubuntu-repo](http://sabnzbd.wikidot.com/install-ubuntu-repo)), there is some mention of starting the program as a service. What exactly would this mean in contrast to simply running the program on start-up, and if it's beneficial, how exactly might it be done?

---

### Post by mssever on 2009-01-09
> **wracktail said:**
> there is some mention of starting the program as a service. What exactly would this mean in contrast to simply running the program on start-up, and if it's beneficial, how exactly might it be done?
Same thing, different term. In the Red Hat world, you use the service command to control init scripts (startup scripts), while in the Debian/Ubuntu world, you run those scripts directly. (Intrepid now provides a Red Hat-style service command, which is awesome.)

---

