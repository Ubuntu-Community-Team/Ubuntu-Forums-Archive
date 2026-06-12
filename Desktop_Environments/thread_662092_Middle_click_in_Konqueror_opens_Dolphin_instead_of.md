---
title: "Middle click in Konqueror opens Dolphin instead of new tab"
date: 2008-01-08
forum: Desktop Environments
---

### Post by MobiusNZ on 2008-01-08
I use Dolphin in my general day-to-day filesystem work, but when I'm dealing with a group of related folders I generally like to pop into Konqueror and use tabs. In 7.04 middle-clicking on a folder would open it in a new tab, but now it opens up a new Dolphin window with that folder. I can right-click on the folder and select "Open in new tab" but I prefer the single click option.
How can I restore this functionality?

---

### Post by samwyse on 2008-01-09
Change the inode/directory mimetype to Konqueror. That will however also make Konqueror the default filemanager instead of Dolphin.

---

### Post by Yellow Onion on 2008-01-09
Try Settings > Configure Konqeuror > web broswer

and under the tabbed browsing heading tick 'open links in new tab ...'

---

### Post by MobiusNZ on 2008-01-09
Hmmm, I don't really want to do that as I quite like using Dolphin most the time. What I don't get is how come Konqueror works fine with left-clicks, but not middle? Konqueror obviously overrides the folder association with left clicks, because the folders still open in it....

There's some logic here that I think I'm missing out on...

---

### Post by Yellow Onion on 2008-01-09
even tho its a webrowser setting it effects the file manager as well

---

### Post by MobiusNZ on 2008-01-09
> **Yellow Onion said:**
> Try Settings > Configure Konqeuror > web broswer

and under the tabbed browsing heading tick 'open links in new tab ...'
That is already ticked, and works fine when using as a web browser - the problem is only when I middle click in file browser mode...

---

### Post by Yellow Onion on 2008-01-09
I was able to recreate this by setting nuatilus as default browser. I cant find anything on google. perhaps report this as a bug on launchpad

---

### Post by Yellow Onion on 2008-01-09
seams to affect any file. middle click ignores the embeded viewer feature. i tested it with an html file same thing happens. normal click open in khtml. but middle click opens in firefox

---

### Post by MobiusNZ on 2008-01-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/181419](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/181419) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've posted a bug about this
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/181419](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/181419)

---

### Post by bailout on 2008-01-09
I installed gutsy yesterday and found this as well and it is annoying.

---

