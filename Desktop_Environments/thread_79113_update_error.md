---
title: "update error"
date: 2005-10-19
forum: Desktop Environments
---

### Post by D_Angle on 2005-10-19
When i try to run update or synaptic i get this following error

W: GPG error: [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy Release: Unknown error executing gpgv
W: GPG error: [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy-updates Release: Unknown error executing gpgv

any ideas?

---

### Post by argosreality on 2005-10-19
[QUOTE=D_Angle]When i try to run update or synaptic i get this following error

W: GPG error: [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy Release: Unknown error executing gpgv
W: GPG error: [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) breezy-updates Release: Unknown error executing gpgv

any ideas?[/QUOTE]It seems to fix the issue if you remove the localized specfic servers. Try this apt-list to see if it fixes the issue:
```

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by D_Angle on 2005-10-19
and how would i go about doing that??

---

### Post by invalid on 2005-10-19
Open a terminal and type:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
sudo gedit /etc/apt/sources.list
```
and replace the contents with the above post.

Cheers,
Cb

---

### Post by D_Angle on 2005-10-19
thanks!

that was a fast response!!! ;) 

Will give it a try.

---

### Post by argosreality on 2005-10-19
Sorry, forgot to post how to actually go about it :)

---

### Post by D_Angle on 2005-10-20
thanks! :) 

It Worked

---

