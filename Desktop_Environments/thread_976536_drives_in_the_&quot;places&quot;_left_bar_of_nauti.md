---
title: "drives in the &quot;places&quot; left bar of nautilus"
date: 2008-11-09
forum: Desktop Environments
---

### Post by beppesbeppe on 2008-11-09
Hi, I haven't found anything about this so here it is:
[[IMG]http://img407.imageshack.us/img407/4214/screenshotfilebrowseraj0.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotfilebrowseraj0.png)

After I upgraded to intrepid those 4 drives circled in blue appeared, and they are totally useless. Even when I insert some external drive a NEW icon appears instead of activating one of those. So, is it possible to get rid of them?

Thanks in advance

edit: when i right-click on them the options "remove" and "rename" are not active

---

### Post by lores on 2008-11-10
A similar problem tends to appear with dmraid. I think there should be a gnome option to permanently hide (and unhide) one of those entries...

---

### Post by cdtech on 2008-11-10
Have you looked in the /media directory? You can just remove the directories from within the /media directory and they will not appear in the Nautilus sidebar.

---

### Post by beppesbeppe on 2008-11-10
nope, unfortunately in /media I've only got the actual mounted partitions and dvddrives

---

### Post by cdtech on 2008-11-10
Are they listed within your "/etc/fstab" file?

---

### Post by beppesbeppe on 2008-11-10
> **cdtech said:**
> Are they listed within your "/etc/fstab" file?
no. In fstab there's only the good stuff.
When I right-click on them there is a "remove" option but very annoyingly it's not available

---

### Post by lores on 2008-11-10
Often (as in case of dmraid), /media/ nor /etc/fstab have nothing to do with nautilus's sidebar, which is the accual problem, as people (prolly devs too) assume it's easy to remove a folder from /media/ and thereby remove the entry, whereas it is not.

---

### Post by BionicSeahorse on 2008-12-19
I also have this problem since I upgraded to Ibex. Any advice on how to remove the extra icon that I have would be great.

BTW, I have a dmraid setup as well, in case that helps. ):P

---

