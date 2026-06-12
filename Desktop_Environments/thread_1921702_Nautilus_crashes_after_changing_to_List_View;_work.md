---
title: "Nautilus crashes after changing to List View; workaround details"
date: 2012-02-07
forum: Desktop Environments
---

### Post by CHONGLISS on 2012-02-07
I'm relatively new Ubuntu.  Running 10.04 LTS. 

- I went to Documents and changed the view to List View.
- Nautilus window crashed
- Tried to open Documents again
- Taskbar showed 'Opening Documents...' for a few seconds
- Nautilus window crashed
- Navigated to Home -> Pictures -> Desktop; all fine
- the navigated to Documents
- Nautilus window crashed

- Found several similar bugs about: [https://bugs.launchpad.net/ubuntu/+source/libdbusmenu/+bug/719591](https://bugs.launchpad.net/ubuntu/+source/libdbusmenu/+bug/719591)
- No admin rights on my machine to upgrade to capture all bug fixes
- Tried to delete nautilus config: rm ~/.nautilus; no success
- Tried changing the default view back to icons for all folders:
- Opened nautilus -> Edit -> Preferences
- Nautilus window crashed

- Cried
- For some reason, went to root around nautlis params / args from Terminal
- Found command nautilus-file-management-properties
- This seems to be the equivalent of Edit -> Preferences; opened fine
- Terminal showed error:

Initializing nautilus-gdu extension

** (nautilus-file-management-properties:4133): CRITICAL **: nautilus_column_chooser_set_settings: assertion `visible_columns != NULL' failed

- Sure enough, in the file management properties / preferences, the List Columns tab had zero columns checked
- So by default, no columns checked and was failing at the above assertion
- Checked one column, closed preferences
- Navigated to Documents; success

---

