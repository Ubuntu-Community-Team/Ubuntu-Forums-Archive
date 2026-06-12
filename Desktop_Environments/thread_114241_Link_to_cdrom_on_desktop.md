---
title: "Link to cdrom on desktop"
date: 2006-01-08
forum: Desktop Environments
---

### Post by MichaëlVD on 2006-01-08
I tried this: right click the desktop, create new, link to device, cd-rom device.

There's nothing in my cd drive.

I want to eject the drive, so I right click the new icon, and I get the following error message:

> The desktop entry file
> /home/michael/CD-ROM Device
> is of type FSDevice but has no Dev=... entry
> <Ok>

I click ok, and the context menu appears, so I can click "eject". This command works.

Why the error message? How can I remove it?

Also, I'm using this way of ejecting because the button on the drive itself never works. Any solutions for that?

Thank you!

---

### Post by Tuf on 2006-01-08
I am not sure but I am guessing that your driver is mounted as /dev/cdrom and your shortcut doesnt reflect that.

I know from konsole I can type  "eject dvd" and the try opens on my dvd drive. If I type "eject dvd -t" it closes.

---

### Post by MichaëlVD on 2006-01-08
You were right; I had to change the location under the Device tab in the properties of the link on my desktop. Thanks.

---

### Post by Tuf on 2006-01-08
Glad it worked! I am a Linux n00b so I am never too sure about anything LoL

---

### Post by Thirsteh on 2006-01-08
You -could- make a shortcut to 'konqueror /cdrom' but that's an absolute alternative. Glad it worked.

---

