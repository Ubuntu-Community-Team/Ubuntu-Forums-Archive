---
title: "[USB] 'Device is now safe to remove' message in 9.04"
date: 2009-05-19
forum: General Help
---

### Post by kpkeerthi on 2009-05-19
Jaunty doesn't seem to notify me "Device is now safe to remove" after unmounting USB flash devices. I'm pretty sure I've seen this message in earlier versions. I came back from Archlinux and the last version of Ubuntu I used was Gutsy.

Does it happen to you or is it just me? Why was it removed?

---

### Post by Egi_Power on 2009-05-19
> **kpkeerthi said:**
> Jaunty doesn't seem to notify me "Device is now safe to remove" after unmounting USB flash devices. I'm pretty sure I've seen this message in earlier versions. I came back from Archlinux and the last version of Ubuntu I used was Gutsy.

Does it happen to you or is it just me? Why was it removed?

I use 8.04 (Hardy) and I don't get this message after I click on *Unmount Volume*.

---

### Post by kpkeerthi on 2009-05-19
Thought I might post this link, incase you were wondering what this message is all about. [http://brainstorm.ubuntu.com/idea/9678/]("http://brainstorm.ubuntu.com/idea/9678/"). So it appears that this was something that infact existed in Ubuntu.

---

### Post by 3rdalbum on 2009-05-19
If there is no delay in unmounting the device (for instance, if you haven't written anything to it, or there is no data that is buffered for sending to the device) then you won't get a notification; it's safe to remove the device when the icon disappears.

If there is an appreciable delay in syncing data, for instance if a file copy has recently taken place and the buffer hasn't been flushed yet, then you will get a notification telling you what is happening ("There is still data being written to the device"), followed by a notification when all data has been synced telling you that it's safe to remove.

---

### Post by kpkeerthi on 2009-05-19
Thanks for clarifying.

---

