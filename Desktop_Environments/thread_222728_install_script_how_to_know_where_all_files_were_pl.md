---
title: "install script: how to know where all files were placed?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by mephisto56 on 2006-07-25
I manually installed the flash plugin for firefox. I did as was told on their website with a simple command. Now I want to know where all the files were placed. As fas as I see, manually installing like these leaves it up to me to remove all files for uninstallation, right?

---

### Post by jordilin on 2006-07-25
Use the command 
```
locate nameoffile
```
where nameoffile could be something like "flash" or "libflash"

---

### Post by mephisto56 on 2006-07-25
And if the script installs a bunch of files without that name?

---

### Post by kdoggfunkstah on 2006-07-25
are there any text files on a system that could possibly keep track of all this stuff? 

I've used the locate command, but it would be nice if there is something out there that would have a full list!

---

### Post by jordilin on 2006-07-25
writing 
```
locate flash
```
will give you all the files that have the string flash on them. If I'm not wrong the package installs libraries, so something like libflash*. But, I'm not a 100% sure. 
If you want to uninstall the flash player, there should be a Readme file in the installation package that tells you how to uninstall. Browsing google I found this link that explains how to do it.
[http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_15380](http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_15380)

---

### Post by endfx on 2006-07-25
> are there any text files on a system that could possibly keep track of all this stuff?

Not that I'm aware of. If you install it using apt or synaptic then yes.
But if you install something manually or using "their" install script, then a record isn't usually kept -- If the company who wrote the software you are installing has any sense at all, they will provide you with uninstall directions.

---

