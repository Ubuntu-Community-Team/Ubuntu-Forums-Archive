---
title: "Popup Notifications in fullscreen VM are annoying. Suggestions?"
date: 2009-06-09
forum: General Help
---

### Post by Lucky75 on 2009-06-09
Hi all,

I'm running 9.04, and for the most part I like the new notification system, even when running pidgin.

However, when i am typing in a fullscreen VM, the popups cause the cursor to lose focus. Is there either a way to stop the focus problem or disable popups ONLY for fullscreen?

I know I can turn all the notiticaitons off for pidgin, but I'd prefer to keep them and just keep focus instead.

Thanks for the help!

---

### Post by kpkeerthi on 2009-06-09
Unfortunately, no. The devs are working hard to improve the notification system for Karmic Koala.

[http://ubuntuforums.org/showthread.php?t=1146489]("http://ubuntuforums.org/showthread.php?t=1146489")

Voice your suggestions here: [https://wiki.ubuntu.com/NotifyOSD/Comments]("https://wiki.ubuntu.com/NotifyOSD/Comments")

---

### Post by Lucky75 on 2009-06-09
Damn, so we need to wait until October to resolve the issue (I hate beta)?  Surely there's some workaround. It's open source for crying out loud lol.

---

### Post by Sinkingships7 on 2009-06-09
> **Lucky75 said:**
> Hi all,

I'm running 9.04, and for the most part I like the new notification system, even when running pidgin.

However, when i am typing in a fullscreen VM, the popups cause the cursor to lose focus. Is there either a way to stop the focus problem or disable popups ONLY for fullscreen?

I know I can turn all the notiticaitons off for pidgin, but I'd prefer to keep them and just keep focus instead.

Thanks for the help!

If you are running the VM with Virtualbox, then you can install Guest Additions to provide seamless mouse and integration.

---

### Post by Lucky75 on 2009-06-09
No, I'm running it in VMware unfortunately. Think I should switch to virtualbox? Could I still use the same image?

---

### Post by kpkeerthi on 2009-06-09
> **Lucky75 said:**
> Damn, so we need to wait until October to resolve the issue (I hate beta)?  Surely there's some workaround. It's open source for crying out loud lol.

There are no workarounds for the new notification system (notify-osd). You may however revert back to the standard notification system (notification-daemon).

1. sudo apt-get purge notify-osd 
2. sudo apt-get install notification-daemon
3. Reboot

---

### Post by Sinkingships7 on 2009-06-09
> **Lucky75 said:**
> No, I'm running it in VMware unfortunately. Think I should switch to virtualbox? Could I still use the same image?

No, VMWare VM's won't run in Virtualbox by default. However, I found this link. It should be able to assist you in converting your .vmdk file to a .vdi one.

[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool)

---

### Post by Chronon on 2009-06-09
Sun's non-OSE version has had VMDK support since version 2.1.

---

### Post by kpkeerthi on 2009-06-09
> **Chronon said:**
> Sun's non-OSE version has had VMDK support since version 2.1.

I second that. There are ways to convert vmware's image to vbox's. Google.

---

### Post by sendblink23 on 2009-06-09
Yup that is true

non related
*Hey kpkeerthi do you know any commands to unmount a hard drive through Live CD?

---

### Post by Lucky75 on 2009-06-09
Isn't it just umount <device>? You can do it through gparted or something too.

---

