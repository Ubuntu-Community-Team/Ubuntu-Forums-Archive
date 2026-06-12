---
title: "Missing Firefox Bookmarks after Ubuntu Update"
date: 2012-05-15
forum: Desktop Environments
---

### Post by aSystemOverload on 2012-05-15
Hi,

My partner's father is running Ubuntu on a rather ancient laptop and he's recently updated to the latest version.  After the update it seems however, that he cannot find any of his Firefox bookmarks and he can't create any new ones.

Any ideas what might of happened and/or how it can be rectified?

I've already tried to un-install and reinstall Firefox, but still nothing.  Another issue, which may or may not be linked is that firefox is saying it cannot perform sync for an unknown reason.

Where would the bookmarks normally be kept?

---

### Post by ajgreeny on 2012-05-15
> **aSystemOverload said:**
> Hi,

My partner's father is running Ubuntu on a rather ancient laptop and he's recently updated to the latest version.  After the update it seems however, that he cannot find any of his Firefox bookmarks and he can't create any new ones.

Any ideas what might of happened and/or how it can be rectified?

I've already tried to un-install and reinstall Firefox, but still nothing.  Another issue, which may or may not be linked is that firefox is saying it cannot perform sync for an unknown reason.

Where would the bookmarks normally be kept?
What was the original version of ubuntu and firefox?

FF keeps all its local configuration info and also the bookmarks backed up in a hidden folder in the user's home as /home/<user>/.mozilla/firefox/[COLOR=Red]qn4bdmr0[/COLOR].default/bookmarkbackups/bookmarks-2012-05-04.json

You can use any of those .json files as a backup to restore the missing bookmarks, but if those files do not exist, or the old version of FF really was very old, you may need to look for a bookmarks.html to restore, still from somewhere in that profile folder..

The value shown above in red will be different on your machine; it is a random alphanumeric, I think, for each profile of FF.

---

### Post by aSystemOverload on 2012-05-16
Not sure what the previous version were specifically, probably just the previous (but up to date) version.  I'm more worried that he can't add new bookmarks (you hover over the start in the awesome bar and it does nothing, same for the menu ADD BOOKMARK.

I'll see if those directories exist, thnx

---

