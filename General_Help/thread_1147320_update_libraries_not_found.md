---
title: "update libraries not found"
date: 2009-05-03
forum: General Help
---

### Post by jackmg on 2009-05-03
I am running Hardy 8.04 remix version on a netbook. I can install packages fine. The problem is updating  through update manager. I NEVER get Ubuntu package update notices. When I run a check update from update manager, the system says that my system is up to date. However, in the software sources panel the first tab (Ubuntu Software) has no checked boxes. In the Third-Party tab numerous entries are checked for the Remix version of Hardy 8.04.

When I check categories in the Ubuntu Software tab and do an update check, I get several error messages (one for each checked item) that says:

ubuntu/sits/hardy/main/binary-iaia/packages.gz 404 not found with an IP address

I notice that I also do not get the upgrade notification for 9.04.

How do I resolve this system update problem? Thanks for your suggestions.

---

### Post by zvacet on 2009-05-03
> in the software sources panel the first tab (Ubuntu Software) has no checked boxes.

That is the reason why your system is up-to-date.Check that boxes (you can leave source unchecked if you want to) and refresh.You will get updates.For getting message to upgrade to next version you have to go to the synaptic>preferences( or settings I don´t know because I don´t use English version)>repositories and set to normal releases instead of LTS.You can not skip versions to upgrade so your upgrade will look like this Hardy>Intrepid>Jaunty.

---

### Post by joeyknuccione on 2009-05-03
Verify:

System > Administration > Software Sources

In that:

Click "Updates" tab

In that, verify the various settings, with attention to the bottom one, "Release upgrade". There you seem to want or need "normal releases" to be the option.

---

### Post by jackmg on 2009-05-03
Thanks for your comments. When I check any of the boxes in the software tab, I get the 404 not found error messages. I've been running this system for the last four months and never have gotten an update alert. I don't mean to a new version. I mean system files to be updated. What am I doing wrong?

---

### Post by zvacet on 2009-05-03
```
cat /etc/apt/sources.list
```

Post output here.

---

