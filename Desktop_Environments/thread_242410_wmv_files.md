---
title: "wmv files"
date: 2006-08-23
forum: Desktop Environments
---

### Post by jimmymac on 2006-08-23
Alright guys,

I'm trying to play some wmv files and having a few problems.  Like it won't play video or audio!
I followed the wiki [here]("https://help.ubuntu.com/community/RestrictedFormats")
and it didn't help.

Any ideas?

TIA

Jimmy

---

### Post by croak77 on 2006-08-23
What player are you using?

---

### Post by jimmymac on 2006-08-23
I've tried vlc, Gxine, Totem and Mplayer.

Cheers,

Jimmy

---

### Post by croak77 on 2006-08-23
For gxine and mplayer, double check to make sure the w32codecs are installed. If they are not;Open a terminal 

```
wget -c http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
```

BTW, what architecture do you have i386, AMD 64, PPC?

---

### Post by jimmymac on 2006-08-23
I'm on i386.
I think I've done that but how do I check anyway?

Cheers,

Jimmy

---

### Post by saracen on 2006-08-23
You can check by opening synaptic (under System->Administration) and then searching for w32codecs.  You should then see whether or not the package is installed and what version it is.

Alternatively if you still have that .deb file that you downloaded (using wget), then you can double click on it and that should open gdebi - the deb package installer for ubuntu.  It will tell you if the package is already installed by saying "Same version already installed".

---

### Post by jimmymac on 2006-08-24
Yeah it's defo installed.

If I try to play it through GXine I get:

Encrypted media stream detected.
Media stream scrambled/encrypted

Which says to me that I don't have the right codecs installed.
It's a DivX file and I've definately got that it's just the wmv support which I should have.

Any other ideas?

MTIA

Jimmy

---

### Post by RAOF on 2006-08-24
> **jimmymac said:**
> ...
Encrypted media stream detected.
Media stream scrambled/encrypted
...

Are you sure the file is **not** encryped?  If it is, you won't be able to play it.  At all.  Yay DRM!

---

### Post by jimmymac on 2006-08-24
Actually to be honest I'm not sure!
Anyway of being able to tell?

Cheers,

Jimmy

---

