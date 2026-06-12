---
title: "Update to OpenOffice 3.1 crahes my system!"
date: 2009-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-05-10
Hi,
i have 8.04 dell mini 9 Ubuntu and i followed these instructions to install oo3:

[http://ubuntuforums.org/showthread.php?p=6576806#post6576806](http://ubuntuforums.org/showthread.php?p=6576806#post6576806)

But after yeseterdays updates to 3.1 it removed openoffice totally, if i install it back then my language /german is not there any more. All that came after message "distribution upgrade", the came some errors...
Any ideas how to install 3.0/3.1 properly?

Thanks

---

### Post by ugm6hr on 2009-05-10
Sorry, I removed the PPA after the initial install with 3.0 (which works fine).

I'm intending to use Jaunty soon, so can't help.

---

### Post by vickoxy on 2009-05-10
> **ugm6hr said:**
> Sorry, I removed the PPA after the initial install with 3.0 (which works fine).

I'm intending to use Jaunty soon, so can't help.

Is there some easy way for me to install OO3.1 and have german language...? I am newbie, so i do not know how to remove this PPA (or you removed official dell´s PPA/or only oo3 ppa?).

---

### Post by ugm6hr on 2009-05-10
> **vickoxy said:**
> Is there some easy way for me to install OO3.1 and have german language...? I am newbie, so i do not know how to remove this PPA (or you removed official dell´s PPA/or only oo3 ppa?).

I don't know, I'm afraid.

Do you still have the .deb files from OO3.0.1 that worked?  If so, try reinstalling them.

I still have them, but don't have any language packs, so don't think they will be of any help to you.

Best to submit a bug to the OO maintainers too.

PS: I only removed the OO PPA (not the Dell repositories)

---

### Post by vickoxy on 2009-05-10
> **ugm6hr said:**
> I don't know, I'm afraid.

Do you still have the .deb files from OO3.0.1 that worked?  If so, try reinstalling them.

I still have them, but don't have any language packs, so don't think they will be of any help to you.

Best to submit a bug to the OO maintainers too.

PS: I only removed the OO PPA (not the Dell repositories)

No, i don´t have any files-i added these repos:
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

and let the synaptic do its job, and it did it very well untill the last updates. I found something here but i am insecure in this method:
[https://www.blogger.com/comment.g?blogID=6823080099887112748&postID=9102386085510705840&page=1](https://www.blogger.com/comment.g?blogID=6823080099887112748&postID=9102386085510705840&page=1)

---

### Post by vickoxy on 2009-05-13
So, is there any way to install OpenOffice 3.0 LPIA (DE) on my Dell Mini? I found on openoffice.org oo3.0 available for download-but it´s non-lpia.

So, if anyone has any suggestions, i´ll appreciate it.

---

### Post by vickoxy on 2009-05-14
SOLVED:

Ok, i found help on german Ubuntu forum:
[http://forum.ubuntuusers.de/topic/openoffice-3-1-funktioniert-nicht/](http://forum.ubuntuusers.de/topic/openoffice-3-1-funktioniert-nicht/)
[http://forum.ubuntuusers.de/topic/openoffice-3-deutsch-ubuntu-8-10/?highlight=openoffic+deutsch](http://forum.ubuntuusers.de/topic/openoffice-3-deutsch-ubuntu-8-10/?highlight=openoffic+deutsch))!

So, actualy, i installed OpenOffice 3.1 from Synaptic, then downloaded german language pack here - [http://ftp.de.debian.org/debian/pool/main/o/openoffice.org/openoffice.org-l10n-de_3.1.0-1_all.deb](http://ftp.de.debian.org/debian/pool/main/o/openoffice.org/openoffice.org-l10n-de_3.1.0-1_all.deb) - because the ones from PPA are buggy/not finished.

That was it. Thanks

---

