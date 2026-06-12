---
title: "Conky Installation Error"
date: 2009-05-03
forum: Desktop Environments
---

### Post by damphoud on 2009-05-03
Hello

I receive this error when installing conky 1.7.0 (error occurs for 1.6.1 as well)

"configure: error: Could not find XdbeQueryExtension in -lXext"

Fresh install of 32bit 9.04, and I've installed the essentials

I've tried to search the web with not much luck... any ideas?

Thanks!

---

### Post by damphoud on 2009-05-03
I installed 1.6.1 from Synaptic... worked fine.

---

### Post by glotz on 2009-05-03
Do you have the **libx11-dev** package?

---

### Post by Uzii on 2009-05-05
Try this:

sudo aptitude install [COLOR=Black]libxdamage-dev[/COLOR]

---

