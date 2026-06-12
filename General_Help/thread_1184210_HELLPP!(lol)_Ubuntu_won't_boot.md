---
title: "HELLPP!(lol) Ubuntu won't boot"
date: 2009-06-10
forum: General Help
---

### Post by osc1882 on 2009-06-10
[[IMG]http://img40.imageshack.us/img40/7613/1002209c.th.jpg[/IMG]](http://img40.imageshack.us/i/1002209c.jpg/)

Man. I have been working the last few days on pimping out Ubuntu for a friend on his new lap top.

I don't know what I did. I was fooling around with a few things and getting over my head alittle. lol.  And the system locked up and I had to turn it off the wrong way ( holding the power button ) and now it won't boot.

Does anyone know what the text on the screen means? Can any one help me fix it? Pretty please? I was really going to bring this to him tonight... Please help guys.

:(

---

### Post by ryanhaigh on 2009-06-10
Just a guess but perhaps the UUID of the partition has changed, did you resize it at all. See here: [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

You could try repairing grub, there are many guides available [this one is for a post windows install fix]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") but should do the job just fine.

---

### Post by osc1882 on 2009-06-10
Thank you ryanhaigh. I'll give that a try with the super grub disk.
if anyone else has any insite, let me know.

---

### Post by osc1882 on 2009-06-10
I used super grub to delete grub and then booted into it again to do a fresh install of grub. Anyone else have any other ideas?

---

### Post by lavinog on 2009-06-11
I agree, your root uuid is wrong.
did you modify /boot/grub/menu.lst?

Can you post it? (use the live cd to read it)

---

### Post by osc1882 on 2009-06-11
When I tried to read the Ubuntu Partition i got this message.

[[IMG]http://img196.imageshack.us/img196/8682/screenshotrxf.th.png[/IMG]](http://img196.imageshack.us/i/screenshotrxf.png/)

---

### Post by osc1882 on 2009-06-11
I told gparted to do a scan and repair of the partion and now it works. Thank you guys very much. You guys rule!!!

---

