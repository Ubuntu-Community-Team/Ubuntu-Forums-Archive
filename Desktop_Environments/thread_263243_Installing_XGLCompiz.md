---
title: "Installing XGL/Compiz"
date: 2006-09-22
forum: Desktop Environments
---

### Post by draco1889 on 2006-09-22
Alright, so I made the switch to Ubuntu (from Gentoo) and I wanted to install XGL/Compiz by following this guide: [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#Installing_nVIDIA_driver](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#Installing_nVIDIA_driver)

I got to the part where it says to run the command
```
sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes csm
```
But when I do, I get the following output:
> Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate
Not sure what this means and Google hasn't been helpful, so I came here.

---

### Post by The Pinny Parlour on 2006-09-22
Sounds like your nearly there.  I did the following:

I went into Synaptic Package Manager and reloaded everything.  I then searched for compiz and cgwd.  It listed a heap of things and I just marked for installation the following:
csm, compiz, compiz-core, compiz-gnome, compiz-plugins, compiz-manager, cgwd and cgwd-themes
Even if I had them installed I marked them for reinstallation.  I had never used the cgwd-themes before, I like them very much.  Make the window borders a darn sight better.

To start, code:
```
compiz-manager
```

---

### Post by draco1889 on 2006-09-22
I get a similar error while trying to install csm:
> Package csm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package csm has no installation candidate
Any ideas?

---

### Post by arsenic23 on 2006-09-22
**WARNING:  This may be the wrong way to fix this.**

But I recon if you exchange the 

deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

with 

deb [http://xgl.compiz.info](http://xgl.compiz.info) dapper main

you might not have this problem anymore.  It's the repo I'm using, anyway.  I'm not familiar with the one in this tutorial.

---

### Post by Darell on 2006-09-23
They deleted their stuff! You have to wait till until al stable version of Beryl is out:(

---

### Post by BLTicklemonster on 2006-09-23
I have compiz-core, compiz-gnome, and that's it. I can't get compiz because

compiz:
 Depends: compiz-plugins but it is not going to be installed

and I can't get plugins because:

compiz-plugins:
  Depends: compiz-core (>=0.0.13.54) but 0.0.13.38-0ubuntu3 is to be installed
 Depends: csm (>=0.5) but it is not installable

and csm is just not anywhere in synaptic

and I can't install compiz-kde because:

compiz-kde:
 Depends: compiz but it is not going to be installed


So I'm sort of stuck in this here loop thing. 

With what I have, will I be able to use compiz? Just log out, then change sessions to it or something?

---

### Post by mindless on 2006-09-23
I had the same trouble this weekend. Eventually I just gave up. It's stupid to remove packages when there is no alternative imo.

---

### Post by nik on 2006-09-23
This is the third tread I'm replying to with this problem... there's a search button at the top of the page...

Anyway, try the compiz forums, compiz and ubuntu are not related.

Yes, packages are removed. Yes, it might seem stupid. QuinnStorm has not yet given any reason for this, but from averything she has done in the past I'm quite sure there is a good reason for this. However, some of the missing packages are uploaded to the compiz forums at 

[http://www.compiz.net/topic-4690-2.html](http://www.compiz.net/topic-4690-2.html)

---

### Post by BLTicklemonster on 2006-09-23
Bah, I've given up that focused interest I had a little while ago. There's nothing to assure success for me, so I don't really care to fiddle around with an unknown that I may or may not use. Not the brightest of ideas to drop support for one thing before you get it's replacement up, but I guess they know what they are doing.

---

### Post by mindless on 2006-09-23
> **nik said:**
> This is the third tread I'm replying to with this problem... there's a search button at the top of the page...

Anyway, try the compiz forums, compiz and ubuntu are not related.

Yes, packages are removed. Yes, it might seem stupid. QuinnStorm has not yet given any reason for this, but from averything she has done in the past I'm quite sure there is a good reason for this. However, some of the missing packages are uploaded to the compiz forums at 

[http://www.compiz.net/topic-4690-2.html](http://www.compiz.net/topic-4690-2.html)

If your post was directed at me for my earlier post, you may have misread because I was requesting an alternate method as I'm not clued up about the GL desktops yet. And it's actually the second time if you felt the need to include this. :p

---

