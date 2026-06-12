---
title: "Dolphin file manager wont open"
date: 2009-12-01
forum: Desktop Environments
---

### Post by lightningfox on 2009-12-01
Hello

My computer is running Kubuntu 9.10 with KDE 4.3.

Today I installed Virtualbox non-ose version from Virtualbox's website, and then I created a virtual machine on my 1tb external hard drive, and installed Windows XP on the virtual machine.

After I installed Windows XP on the virtual machine, Dolphin stopped
opening. I clicked on Dolphin's icon many times but still it didn't open.

I rebooted my computer and tried opening Dolphin, but it still wouldn't open.

I can open all my other programs besides Dolphin.

Why is this happening and how can I fix it?

---

### Post by captaincrook on 2009-12-01
Try opening from a terminal and see what the output is. Simply type "dolphin" in (no quotes).

---

### Post by lightningfox on 2009-12-02
Hello

Here is the output when I type dolphin in the terminal:

```
<unknown program name>(4657)/: Communication problem with  "dolphin" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." "
```



Also, now Firefox isn't opening either.

Here is the output when I type firefox in terminal:

```
Could not find compatible GRE between version 1.9.1 and 1.9.1.*.
```

Please help me fix this problem.

---

### Post by captaincrook on 2009-12-02
I'm no whiz here but that dolphin stuff looks like dbus might not be running. For Firefox, those numbers look like its xul-runner related. I am unsure, just offering my two cents here.

---

