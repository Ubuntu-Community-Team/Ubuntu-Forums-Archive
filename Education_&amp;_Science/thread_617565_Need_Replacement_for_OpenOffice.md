---
title: "Need Replacement for OpenOffice"
date: 2007-11-19
forum: Education &amp; Science
---

### Post by LaneLester on 2007-11-19
I've been a fan of OpenOffice for years, in both Ubuntu and Windows. It's been both powerful and stable.

That is not true for Kubuntu Gutsy and OO 2.3. OO crashes repeatedly while I'm using it. As far as I can tell, this happens when I'm typing in an area where there is already some text below the cursor. I've searched various forums and haven't seen this among the frequent-crashes posts.

OO and Kubuntu are, for me, tools, not a hobby. I've reinstalled OO once, since someone somewhere said it helped them. It didn't help me.

I'll keep using OO to format final documents, but I'm going to have to find something else for the creation phase. Maybe AbiWord or KOffice will save to OO formats. Or maybe I'll just use Gedit. :(

Lane

---

### Post by por100pre1 on 2007-11-19
Abiword will do, but KOffice has better ODT support and uses Qt of course. Try renaming the OOo settings profile to troubleshoot OOo:

```
mv .openoffice.org2 .openoffice.org2_backup
```

---

### Post by LaneLester on 2007-11-19
Thanks for the suggestion. I went ahead and installed AbiWord, but as you note, it doesn't provide support for ODTs. It does do DOC, though. I put off installing Koffice, because of its size, but I think I'll give it a shot.

And I'll try the profile switch. I hate to lose all my customizing, but if it eliminates this nuisance, it will be worth it. At least I can put everything back if it doesn't do any good.

Lane

---

### Post by sam81 on 2007-11-20
I think there is a plugin that allows open/save odf for abiword, look into the abiword-plugins package. I'm not sure how good the plugin is though.

---

### Post by Wiebelhaus on 2007-11-20
Not to try and Hijack , But what's up with the ODT people shutting their doors is this bad or will IBM just pick it up.

---

### Post by LaneLester on 2007-11-21
Thanks, sam81 and others who have posted on-topic. :)

Speaking of plugins, I'm thinking now that a plugin has been the cause of my OO woes. I removed several called "writer's tools," and the problem seems to have gone away.

Lane

---

