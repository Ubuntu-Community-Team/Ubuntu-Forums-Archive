---
title: "file-manager: always open a konqueror tab"
date: 2005-05-14
forum: Desktop Environments
---

### Post by suoko on 2005-05-14
Hi,
I'd like to solve this problem with konqueror: after I insert a CD and clic on the relative desktop icon, if konqueror is alredy open, konqueror opens tab allowing me to browse the cd folder.
Now, I'd like konqueror to open a new konqueror window instead of tab, with all my custom file-maganer settings (i.e. the left tree pane).

Any suggestions?
thanks

---

### Post by govert on 2005-05-15
[QUOTE=suoko]Hi,
I'd like to solve this problem with konqueror: after I insert a CD and clic on the relative desktop icon, if konqueror is alredy open, konqueror opens tab allowing me to browse the cd folder.
Now, I'd like konqueror to open a new konqueror window instead of tab, with all my custom file-maganer settings (i.e. the left tree pane).

Any suggestions?
thanks[/QUOTE]

Try:
Konqueror-> 
  Settings -> 
     Configure Konqueror -> 
        Web Behaviour -> 
           Tabbed Browsing:Advanced Options:
parameter 
"Open as tab in existing Konqueror when URL is called externally" : FALSE
*phew*

Let me know if it works.


It's a mystery to me that this was not set as default.


/govert

---

### Post by suoko on 2005-05-19
I actually solved it modifying "association files" -> "inode" -> "directory" setting "kfmclient openProfile filemanagement"

---

