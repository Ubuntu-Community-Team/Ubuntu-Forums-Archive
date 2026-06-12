---
title: "Desktop Icons in Xubuntu (floppy &amp; iPod)"
date: 2007-05-05
forum: Desktop Environments
---

### Post by h0bbe on 2007-05-05
I have two problems about desktop icons on my newly installed xubuntu feisty system.

1. I don't want the floppy drive visible while not in use, can I get rid of it?

2. When I connect my iPod I get two icons on my desktop, one with the name I gave my iPod when I set it up, and thats fine. I also get one named "Apple iPod Music Player" which is unmounted and returns an error message when double-clicked, can I get rid of it?

Thanks for any help!

---

### Post by jjalocha on 2007-05-21
I think, I have a related problem. I don't like that Xubuntu Feisty puts icons on the desktop by default (File System, Trash, Home). Anyone knows how to disable that?

What I surely DO like, is the icons of removable devices (CDs, USBs) showing up on the desktop, which works fine for me. I like to mount/unmout/eject them with right-click.

Not so sure about the floppy, since I don't have a drive.

I also have an unmounted hard-disk partition icon showing up on the desktop, which is annoying. Is it regarded in this case as a removable device?

---

### Post by h0bbe on 2007-05-21
You can change which icons to be shown in desktop settings!

---

### Post by jjalocha on 2007-05-21
Yes, I just checked, and you're right, this should work. -- But this tool seems to be buggy! After fiddling with the check-boxes, all icons disappeared, except the trash icon.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=33115&stc=1&d=1179786562[/IMG]
But never mind. I'm sure it will be fixed with time.

---

### Post by voided3 on 2007-05-22
If you don't have a floppy drive installed, disable your floppy controller in BIOS (typically under "integrated peripherals" and listed as "onboard FDD controller"). If Xubuntu sees there is no controller or drive, there will be no icon. Also, a floppy drive is put in the same category as USB drives and CDROMs so disabling removable media on the desktop gets rid of that too. Good luck!

---

### Post by eeried on 2007-06-01
Okay, but the only option in Desktop settings is to disable all icons. Choosing which icons you want doesn't seem to work -- or should you log out and in again for the changes to take effect?? rather unlikely!

If you disable all icons and when you plug a USB key for instance it doesn't show, which is inconvenient -- as it's easier to umount the USB key when there's an icon on the desktop.

> What I surely DO like, is the icons of removable devices (CDs, USBs) showing up on the desktop, which works fine for me. I like to mount/unmout/eject them with right-click.
Same here!
I get all the icons for my unmounted volumes (I'm dual booting Xubuntu and Debian Etch) and I just hate that clutter.

Xfce has improved a lot since Dapper but those icons are a pest. And have you noticed a silly message pops up when you've unmounted your USB key, at least it does sometines, not typically, and it looks like the moronic message you get on a Windows box -- now what's happening?? We don't want something looking like windows, do we? We want easy Linux (we've got that already) but no lookalike.

---

### Post by domer on 2007-06-12
When I plug in my USB key I can read-write from the drive, but the usb key icon stopped appearing on the desktop. Can someone tell me how to show the icon on the desktop. It is so much easier to eject the USB key if the icons appears on the desktop. Thanks.

---

### Post by domer on 2007-06-12
> **jjalocha said:**
> I think, I have a related problem. I don't like that Xubuntu Feisty puts icons on the desktop by default (File System, Trash, Home). Anyone knows how to disable that?

What I surely DO like, is the icons of removable devices (CDs, USBs) showing up on the desktop, which works fine for me. I like to mount/unmout/eject them with right-click.

Not so sure about the floppy, since I don't have a drive.

I also have an unmounted hard-disk partition icon showing up on the desktop, which is annoying. Is it regarded in this case as a removable device?

I had a similar problem of unnecessary icons showing up on my desktop. But I use Ubuntu Dapper. In my case, this fixed the issue:
- Press Alt + F2
- In the "Run Application" window type **gconf-editor**
- Then in the configuration editor (the window that opens) browse to **[COLOR="Red"]apps[/COLOR]** -> **[COLOR="Red"]nautilus[/COLOR]** -> **[COLOR="Red"][COLOR="Red"]desktop[/COLOR][/COLOR]** and uncheck icons you do not need.

---

### Post by eeried on 2007-06-13
There should be a way though in Xubuntu. i had a look at a file and change things there but no change on the Destop. perhaps changes take effect after logging out and in again (or restarting X)?

This is the content of my /.config/xcfe4/icons.screen0.rc
```
[File System]
row=1
col=1

[Home]
row=6
col=0

[Trash]
row=5
col=0

[Floppy Drive]
row=4
col=0

[3G Volume]
row=3
col=0

[/home]
row=2
col=0

[301M Volume]
row=1
col=0

[46M Volume]
row=0
col=1

[IOMEGAMINI]
row=3
col=0

```

My USB key IOMEGAMINI isn't plugged in now.
In the same folder the file, xfdesktoprc,  says 
```
[file-icons]
show-removable=true
```

So why not try removing the icons we don't need, and the removable devices should still show up as icons on the desktop.
;)

---

### Post by voided3 on 2007-06-17
I've found what works is to first enable all icons, then disable and re-enable XFCE to manage the desktop with the checkbox on desktop prefs. Then uncheck what you don't want, then reset the XFCE desktop again as above. If that doesn't work, try disabling one thing at a time; if I recall that may have been how I did it. Good luck!

---

### Post by MyR on 2008-05-28
> **voided3 said:**
> I've found what works is to first enable all icons, then disable and re-enable XFCE to manage the desktop with the checkbox on desktop prefs. Then uncheck what you don't want, then reset the XFCE desktop again as above. If that doesn't work, try disabling one thing at a time; if I recall that may have been how I did it. Good luck!

thanks this works for me

---

