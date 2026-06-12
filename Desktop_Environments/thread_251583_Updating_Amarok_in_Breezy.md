---
title: "Updating Amarok in Breezy"
date: 2006-09-05
forum: Desktop Environments
---

### Post by eeefresh on 2006-09-05
Sorry to post this on the Dapper boards, but I wasn't sure if anyone still read the Breezy forums.

I recently switched back to Breezy from Dapper since I was one of the unfortunate ones receiving [system lockups]("http://www.ubuntuforums.org/showthread.php?t=193283&highlight=Firefox+locks").  Now when I try to install Amarok, the only version in the repositories is 1.3.  Is there a way to install the latest version?

I'm still a Linux newbie, so specific instructions would be appreciated!

---

### Post by elettronicha on 2006-09-05
Just read yourself: [http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

---

### Post by eeefresh on 2006-09-05
Does it matter that these instructions are for Kubuntu and Ubuntu?

---

### Post by elettronicha on 2006-09-05
I think Amarok is only in the Kubuntu repository, though I'm not sure, but obviously one can install Amarok under Ubuntu. The problem isn't that but, as you can read:
> Packages are available for i386, PowerPC and AMD64. Amarok 1.4 can not easily be supported on Kubuntu 5.10 (breezy) because it needs a newer version of taglib.

---

### Post by eeefresh on 2006-09-05
So I take it you can't install the newer version of taglib on 5.10?

---

### Post by elettronicha on 2006-09-06
I don't know. It's worth a try, follow those instructions and type:

$ sudo apt-get update
$ sudo apt-get -s install amarok

Don't install a thing! Just let us see the result.

---

