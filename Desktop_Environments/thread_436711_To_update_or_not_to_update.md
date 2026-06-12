---
title: "To update or not to update?"
date: 2007-05-08
forum: Desktop Environments
---

### Post by Znupi on 2007-05-08
I have installed Beryl on my Ubuntu Feisty (it's just amazing, but that's not the point) using the tutorial at [https://help.ubuntu.com/community/Beryl/ATI/Feisty](https://help.ubuntu.com/community/Beryl/ATI/Feisty) . But right now I'm in doubt because at the end of the tutorial I had to 'downgrade' Beryl, but now my Update Manager offers me to update Beryl (beryl-core, emerald and libemeraldengine0). Should I install these updates? :confused:

---

### Post by mcduck on 2007-05-08
> **Znupi said:**
> I have installed Beryl on my Ubuntu Feisty (it's just amazing, but that's not the point) using the tutorial at [https://help.ubuntu.com/community/Beryl/ATI/Feisty](https://help.ubuntu.com/community/Beryl/ATI/Feisty) . But right now I'm in doubt because at the end of the tutorial I had to 'downgrade' Beryl, but now my Update Manager offers me to update Beryl (beryl-core, emerald and libemeraldengine0). Should I install these updates? :confused:

the guide tells you to downgrade the package, and then lock it.. if you do that, you don't have to worry about getting updates to that package :)

edit: sorry, wrong guide :D. Anyway, just lock the package you downgraded. (in synaptic, select the package & go to Package/Lock Version

---

### Post by Znupi on 2007-05-08
Ok so I locked the beryl-core package. Should I lock the other two, too? (emerald and libemeraldengine0) Or is it safe to install them?

---

### Post by mcduck on 2007-05-08
Yes, that should be safe.

Besides, if that gives you any troubles you can always just downgrade them back to the versions you have now..

---

### Post by Znupi on 2007-05-08
Thanks, I updated with no problem :)

---

