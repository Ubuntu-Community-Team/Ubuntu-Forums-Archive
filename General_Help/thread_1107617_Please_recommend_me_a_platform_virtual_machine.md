---
title: "Please recommend me a platform virtual machine"
date: 2009-03-26
forum: General Help
---

### Post by Pidgin on 2009-03-26
I mainly use Ubuntu. In some cases I have to use Windows XP, and I need several Windows XP separated for security reasons. So I need a virtual machine that supports **branch snapshot** in order to save hard disk space. I already know that VMware Workstation can do that. But it is not free. However, the famous Sun xVM VirtualBox cannot handle that at present.
Could someone please recommend me a good virtual machine that supports branch snapshot?
Thank you!

---

### Post by Xiong Chiamiov on 2009-03-27
Are you sure VirtualBox doesn't?  It can do quite a lot, and is in fairly heavy development.

What about the free version of VMware?

---

### Post by albandy on 2009-03-27
could you define what's exactly branch snapshot? VirtualBox have take snapshot option that lets you take snapshots of the execution state and reverting to an old one if something fails and you want to undo what you did

---

### Post by Pidgin on 2009-03-28
> **Xiong Chiamiov said:**
> Are you sure VirtualBox doesn't?  It can do quite a lot, and is in fairly heavy development.

What about the free version of VMware?

I am sure VirtualBox cannot do that now. Because I know that they are working on that.
The free version of VMware is too weak.

---

### Post by Pidgin on 2009-03-28
> **albandy said:**
> could you define what's exactly branch snapshot? VirtualBox have take snapshot option that lets you take snapshots of the execution state and reverting to an old one if something fails and you want to undo what you did

Please look at the image below. As you see, snapshots are organised like a tree. While in VirtualBox, it is just a line.
[IMG]http://upload.wikimedia.org/wikipedia/en/9/99/VMware_Workstation_-_Snapshot_Manager.png[/IMG]

---

