---
title: "openoffice special character (à) display problem: weird!"
date: 2008-02-14
forum: Desktop Environments
---

### Post by wgw on 2008-02-14
Recently (as of about 2 months, perhaps when I upgraded to Gutsy... not sure) my openoffice files with extended ascii characters, àéë etc, have been displaying as weird characters: ç is displayed as Á; à as a double choss, É as ... and so on. 

This seems to only happen in openoffice documents, and only the text part, not the menus. 

And, sometimes it seems to work for some characters, then it goes back to weird characters. Some more weirdness:

If I bold the character, it becomes normal.
All characters display correctly under gedit, in the same font (times new roman)
I reinstalled ms core fonts, and core files for openoffice. At first I thought I had fixed it, but it is back again (after reboot). 

Again in openoffice, menus display correctly; the only problem is in the text, whether created on the spot or created years/months/days ago (not a text entry problem). 

If I paste à from another application, it is transformed into the wonky double cross; unless I bold it, in which case revoilà à

:shock: :confused:

Any ideas?

---

### Post by wgw on 2008-02-15
I think this is the bug: 
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/173090](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/173090)

Will follow that bug fix.

---

