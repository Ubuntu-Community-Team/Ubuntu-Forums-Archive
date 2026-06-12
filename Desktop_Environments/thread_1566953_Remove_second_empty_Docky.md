---
title: "Remove second empty Docky?"
date: 2010-09-03
forum: Desktop Environments
---

### Post by volkerbradley on 2010-09-03
I clicked on the anchor in Docky and then clicked on New Dock.
This created a second dock which is empty.
I want to remove this second empty dock.
How is that done?
Thanks.

---

### Post by volkerbradley on 2010-09-08
In case you have removed the Docky item, you need to reenable it to do this.  Once the Docky item is reenabled, remove the second dock easily by clicking on the unwanted second dock and then clicking on the Delete button in the Docky item.

---

### Post by codeice on 2010-10-26
Similar prob for me, however in my case the new spurious dock has positioned itself underneath the launcher panel on the left hand side of the screen and cannot be accessed.

I am using 10.10 Maverick Meerkat on a HP 5120 Mini. It would appear that with 10.10 there is currently no facility to disable, even temporarily, the launcher panel (see thread [http://ubuntuforums.org/showthread.php?p=9979813](http://ubuntuforums.org/showthread.php?p=9979813)) and so at the moment I am stuck with another Dock. Unless anyone has any ideas?

Thanks

---

### Post by Gaba_p on 2011-02-11
Since the owner changed the status to [SOLVED] but the solution is nowhere to be seen, I'll show what I did to fix this.

- upgrade to the latest version of docky.
- Follow this instructions:
* Press Alt + F2
* Type command gconf-editor and hit enter/return
* Navigate to “apps/docky-2/docky/DockController/ActiveDocks” in the gconf-editor
* Remove the second dock.
* Restart Docky

Here is the site I got the instructions from: [http://goo.gl/DcLZn](http://goo.gl/DcLZn)

PD: I STILL can't create a second dock without it being empty (and thus unusable) and I STILL can't uncheck 'manage windows without launcher'...

---

