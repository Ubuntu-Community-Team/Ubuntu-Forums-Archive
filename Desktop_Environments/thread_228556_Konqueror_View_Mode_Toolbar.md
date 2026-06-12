---
title: "Konqueror View Mode Toolbar"
date: 2006-08-03
forum: Desktop Environments
---

### Post by jonnymccullagh on 2006-08-03
I recently upgraded from breezy to dapper and in Konqueror on breezy I have a few icons in the 'Main' toolbar for switching to Icon view/Detailed view/Image View.

I prefer to always browse using Detailed view (which also has a habit of randomly reverting back to icon view on its own) and if necessary manually click that 'Icon View' button on the toolbar. But dapper does not have it. I have tried 'Configure Toolbars' but there is no option to add it.

When I check back to breezy I see that under Configure Toolbars the option is:
ActionList.viewmode_toolbar
This option can be removed but cannot be re-added or amended.

Is there any way I can add this option to Dapper?
thanks in advance,
j

---

### Post by jonnymccullagh on 2006-08-08
Answering myself here - hopefully it will benefit others.

I edited: /home/me/.kde/share/apps/konqueror/konq-kubuntu.rc

I added:  <ActionList name="viewmode_toolbar" />
under the section for the main toolbar i.e. line 84

I think it may also be possible to edit it under: /usr/share/apps/konqueror/

I can't believe this has been removed with no GUI method for adding it.

---

### Post by editrix on 2006-08-09
> **jonnymccullagh said:**
> Answering myself here - hopefully it will benefit others.

Yes, it has. Thanks for posting.

> **jonnymccullagh said:**
>  I can't believe this has been removed with no GUI method for adding it.

Some very strange things have been removed from both K and G with Dapper. Whatever happened to: If it ain't broke, don't fix it?

---

### Post by gertjan_hofman on 2006-08-13
Much appreciated. I just spent 30 min trying to do the same....

Gertjan

---

