---
title: "Ubuntu will not startup"
date: 2009-04-08
forum: General Help
---

### Post by stukpixel on 2009-04-08
I rebooted to enable some minor changes, and then it told me that I had booted up 28 times therefore it would need to do a disk check.

It does one, spits back a huge amount of errors(I know this already; my drive is defective, but ubuntu worked well regardless), and then tells me that a manual fcsk must be performed before sending to me to the command prompt as root.

Now whenever it starts up, it forces a disk check since it says "problem in the file system". How can I skip this, as I know ubuntu will boot up perfectly even though there are problems?

---

### Post by 3Miro on 2009-04-08
Your drive is about to die any minute. Use the LiveCD to backup whatever you have that is important (you don't want to loose your family photos and such). Then get a new drive.

Even if there is a way to bypass the scan, the system might still not work. It will be slow at best and will probably constantly crash because of errors.

Even if Ubuntu worked fine before, it might be the case that more of the HD went bad and more data was corrupt in the mean time.

---

### Post by stukpixel on 2009-04-08
Ubuntu seems to have ignored them until the check (worked pretty well), so I blame the check disk for making it unbootable as well as my defective hard drive.

EDIT: I'm working on my laptop using my backup usb, is there any file I can change which will skip the force check?

---

### Post by stukpixel on 2009-04-08
okay. I fixed the force check and it boots up normakky.

I set it off by going into the etc folder and change the value "errors" to continue, as well as switching fcsk off entirely.

---

