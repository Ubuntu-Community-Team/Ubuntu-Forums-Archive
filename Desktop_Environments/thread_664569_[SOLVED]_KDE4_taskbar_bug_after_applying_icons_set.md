---
title: "[SOLVED] KDE4 taskbar bug after applying icons settings"
date: 2008-01-11
forum: Desktop Environments
---

### Post by diskace on 2008-01-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gxmms/+bug/182034](https://bugs.launchpad.net/ubuntu/+source/gxmms/+bug/182034) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a bug with KDE 4.0 on kubuntu 7.10

I tried modifying some of my desktop icons. When you right click on an icon (in my case XMMS) under icons settings the window that is popping has a PREVIEW tab. I accidently managed to click on that tab and since then the KDE taskbar disappeared from the desktop. 

Here is my bug report:

It says: The application PlasmA workspace (plasma) crashed and caused the signal 11 (SIGSEGV)

 I rebooted the pc but now the taskbar is not loading.


Any ideas ?

Thanks

---

### Post by .nedberg on 2008-01-11
Hi

I am using kde4 with Hardy (8.04). I had a similar problem. Solved it by issuing
```

rm -rf ~/.kde4

```

This will remove all your kde4 related settings. Don't use it if you don't mean it! :)

I also have kde3 so it was not a problem for me.

---

### Post by diskace on 2008-01-13
nedberg that fixed my problem. Removed all kde4 settings using:

rm -rf in the /home/(my username)/.kde4 directory
reboot

And everything was back.

Thanks !

---

### Post by bruceli on 2008-01-14
it resolves my problem either. thanks!

---

### Post by Ramorous on 2008-01-14
> **diskace said:**
> reboot

Reboot? ack... try Ctrl-Alt-Backspace first before rebooting. This keystroke will restart the display manager.

---

