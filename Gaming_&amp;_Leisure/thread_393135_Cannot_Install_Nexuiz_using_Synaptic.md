---
title: "Cannot Install Nexuiz using Synaptic"
date: 2007-03-25
forum: Gaming &amp; Leisure
---

### Post by niglch on 2007-03-25
I tried installing Nexuiz (version 2.2.3-1~edgy1) using add/remove programs on Edgy Eft and received the following error: ```
This application conflicts with other installed software. To install 'nexuiz' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.
``` So, I opened up synaptic and searched for Nexuiz and marked it for installation to see what would happen and got this error:
```
Could not mark all packages for installation or upgrade
The following packages have unresolvable dependencies. Make sure all repositories are added and enabled in the preverences

nexuiz:
 Depends: nexuiz-data but it is not going to be installed 
``` I checked my preferences making sure I had main, restricted, universe, and multiverse enabled, and they were. I then saw the missing "nexuiz-data" package sitting right under Nexuiz and marked it for installation and then tried marking nexuiz again. I got a similar error about unresolved dependencies, but this time it read: ```
nexuiz:
  Depends: nexuiz-data (>=2.2.3-1) but 2.2.3-1~edgy1 is to be installed
``` But wouldn't that be the same version except for the ~edgy1 thing? Is there any way to get around this?

---

### Post by ksenos on 2007-03-25
I got the same issue here. Any solution?

---

### Post by Matt Yun on 2007-03-25
I'm running Feisty-beta now, and I just installed Nexuiz with aptitude, no problem ie. aptitude install nexuiz

---

### Post by mrThefter on 2007-03-25
I had the same problem
So I just downloaded it off the official site. =\

---

### Post by niglch on 2007-03-25
Could it just be a mistake in the edgy-backports database (like they put in the wrong dependencies)? I disabled the backports repository and was able to install the previous version of  Nexuiz without an issue.

---

### Post by deepwave on 2007-03-25
No problems here either.  I installed nexiuz on Edgy a few days ago, and upgraded to Feisty yesterday... and no issues with Synaptic.

---

### Post by Jarn on 2007-03-25
Yep, it's from ubuntu-backports. I was having this problem too, then I commented that out of my sources.list. Then, after an apt-get update, it worked.

---

### Post by 16777216 on 2007-03-26
I just want to update, some one needs to fix the package.
Is there any way to force it?

---

### Post by Dylnuge on 2007-03-26
Just remove/disable the backports database from your repo list.

It's under software sources.

---

### Post by cezz on 2007-03-27
> **Dylnuge said:**
> Just remove/disable the backports database from your repo list.

It's under software sources.
You can also force *nexuiz-data* and *nexuiz-music* to older version.. (CTRL+E or Package->Force version) in synaptic. It should work.

---

### Post by 16777216 on 2007-03-27
The problem is I wish to ***_upgrade_*** not _***downgrade***_. :(
It's not a big deal, I would just like to have the newest version as these guys almost always improve the game quite a bit with every update.
Oh well, manual install time. :)

---

