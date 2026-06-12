---
title: "OpenOffice Scheme"
date: 2009-03-15
forum: General Help
---

### Post by AgentZ86 on 2009-03-15
Hi

I have 8.10 Open office 2.4 and attempted to follow instructions to upgrade to 3.0

I had some dependency messages and OpenOffice was not listed in the menu or installed as it would seem.

Anyhow I removed the Intrepid Repository and uninstalled all the OpenOffice stuff.

I re-installed 2.4 for the ADD/Remove section and also had to install helper-english because the help menu's did not work after re-install.

The question is ? How do I get the original 2.4 OpenOffice Scheme back which matches the Ubuntu format. 

My new installation of 2.4 looks different then it did before with dark grey menu's etc.

How can I get back to the way it looked before ?

Please advise
Thanks

---

### Post by Zill on 2009-03-15
OpenOffice menu Tools, Options:

OpenOffice.org
   View

Set Icon Style and Size to your preference of Default or Automatic etc.

---

### Post by AgentZ86 on 2009-03-15
> **Zill said:**
> OpenOffice menu Tools, Options:

OpenOffice.org
   View

Set Icon Style and Size to your preference of Default or Automatic etc.

Thanks

For some reason no changes take place when I make any selections here.

Can't change color or fonts either ? Strange.

---

### Post by Zill on 2009-03-16
AgentZ86:  You could try renaming your hidden user config directory (.openoffice.org2) so that this remains available as a backup.

```
mv ~/.openoffice.org2 ~/.openoffice.org2_bak
```

Restart OpenOffice and then a new (default) .openoffice.org2 directory should be created.  You will have lost any existing preferences in the old directory but these could be recreated if necessary.

---

### Post by calc on 2009-04-06
It probably looks wrong because you need either openoffice.org-gnome or openoffice.org-kde (depending on your desktop) and that package is not currently installed.

---

