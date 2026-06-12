---
title: "Xara Lx problems"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Kashirigi on 2006-08-28
I've downloaded the latest version of Xara from [http://www.xaraxtreme.org/download/](http://www.xaraxtreme.org/download/)

The autopackage installs fine on both my laptop and desktop, and works like a charm on my desktop computer.

However, on the laptop, when I start xaralx all I get is this:

paul@Gernsback:~$ xaralx
Aborted

It's not very helpful. Does anyone have any hints as to how I can find out what's happening? Or, ideally, a solution that will have Xara run.

Thanks.

---

### Post by cptnapalm on 2006-08-28
<No useful information>
Programs should be very noisy when they die like that...  That way the error messages can be.. you know... useful.
</No useful information>

---

### Post by Kashirigi on 2006-09-26
Here's what I eventually came up with -- it's also on the XaraLX forums.

I have made a cludgy hack to "solve" the problem. I haven't played around with it, but at least it will start now. I won't have Japanese input in Xara, but I can live without it, at least for now.

make a new file called xaralx.sh, and make it's contents like this:

#! /bin/bash
unset XMODIFIERS
unset GTK_IM_MODULE
unset QT_IM_MODULE
/usr/bin/xaralx &
export XMODIFIERS=@im=SCIM
export GTM_IM_MODULES=scim
export QT_IM_MODULES=scim


instead of running xaralx, use sh ./xaralx.sh

I certainly can't guarantee that this will work on every system. It does, however, make xara start on mine.

---

