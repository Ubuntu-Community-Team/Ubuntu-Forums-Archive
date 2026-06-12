---
title: "PCManFM right click context menu &quot;Create New&quot; Folder how to remove orphaned entries"
date: 2019-04-10
forum: Desktop Environments
---

### Post by roler2 on 2019-04-10
Is there a way of removing the orphaned entries located in "Create New" Folder of the PCManFM right-click context menu?

Any assistance would be appreciated. Thank you!

---

### Post by again? on 2019-04-10
Not sure where all the entries are coming from but you can specify user only
scripts from ~/Templates.
pcmanfm > preferences > advanced > templates

**[COLOR="#FF0000"]Edit:[/COLOR]** If you are using Xubuntu, the extra entries in pcmanfm may be coming from **/usr/share/xubuntu/templates**
In Xubuntu, I could remove the pcmanfm extra entries by renaming the templates folder.
```
sudo mv /usr/share/xubuntu/templates/ /usr/share/xubuntu/templates.bak
```

---

### Post by roler2 on 2019-04-17
The entries appeared to be located within orphaned Templates Folders. I deleted the respective Folders and then the orphaned entries also disappeared. Thank you for your assistance!

---

