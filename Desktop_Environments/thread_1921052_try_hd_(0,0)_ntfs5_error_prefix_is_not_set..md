---
title: "try hd (0,0) ntfs5 error prefix is not set."
date: 2012-02-06
forum: Desktop Environments
---

### Post by mohittomar13 on 2012-02-06
Hi everyone...

This is the first time iam using ubuntu on my desktop pc and also the first time using ubuntu forum.

Well, after installing ubuntu 11.10 on my pc using wubi i get an error while booting up it says try hd (0,0)ntfs5 error prefix is not set. Please help to resolve this error.

thnaks in advance.:) :)

---

### Post by bcbc on 2012-02-06
Is it booting Ubuntu? If it is then don't worry about it.

The message is actually normal:
"Try (hd0,0)": diagnostic message issued by the tool used to boot wubi.
"error 'prefix' not set": a diagnostic from grub that shouldn't be issued - but it has been since 11.04 was released on all wubi installs. Not indicative of any problem.

If, on the other hand, it's not booting, then that's a different story and completely unrelated to the messages you are seeing.

---

### Post by max313 on 2012-03-28
i tried to install 11.10 using windows installer (wubi) after resstart i get this error in a black screen and the only way to get out of it is to get back to windows after manual shutdown!
what should i do?

---

### Post by bcbc on 2012-03-28
> **max313 said:**
> i tried to install 11.10 using windows installer (wubi) after resstart i get this error in a black screen and the only way to get out of it is to get back to windows after manual shutdown!
what should i do?

Probably the best is... create a new thread, post your machine specs (brand/model/graphics card). Make sure you wait a couple of minutes to rule out the problem that some people have (delayed booting). If you get some diagnostic other that the prefix not set message, please include that in your post.

If Ubuntu runs fine from a live CD/USB it should work fine with Wubi, so you can try that as well.

There's no error I know of that would leave you hanging at the 'error prefix not set' message. But some people have reported delays in booting at this point.

---

### Post by max313 on 2012-03-29
oh sure but last try before a new topic, 
does wubi work with virtual disks? i mean does it copy everything to the destination before restarting? i used virtual clone drive to mount the iso file! is it fine?

---

### Post by bcbc on 2012-03-29
> **max313 said:**
> oh sure but last try before a new topic, 
does wubi work with virtual disks? i mean does it copy everything to the destination before restarting? i used virtual clone drive to mount the iso file! is it fine?

Yes that works (it copies the ISO to the destination 'drive' during the install) although I've never tried it as it's unnecessary: you can place wubi.exe in the same directory as the desktop CD ISO and run wubi from there. It will find the ISO and use it.

---

