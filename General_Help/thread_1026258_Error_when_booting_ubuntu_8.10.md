---
title: "Error when booting ubuntu 8.10"
date: 2008-12-30
forum: General Help
---

### Post by baddison on 2008-12-30
I am getting the following error which is preventing Ubuntu 8.10 from booting properly into GUI:
[ 33.120883] b43-phy0 error: PHY transmission error
followed by a few more of these error messages.

I suspect that I'm getting this error message because of my Audigy 2 zs notebook sound card which will not work properly in 8.10. When I boot into recovery mood I get several error messages that look like this:
ALSA lib confmisc.c:768parse_card) cannot find card 'Audigy 2'

All of my troubles began after upgrading Ubuntu from 8.04 to 8.10. Note my Audigy 2 sound card works perfectly fine in windows vista and when I was using Ubuntu 8.04.  I hope this does not mean I need to reinstall ubuntu.

Any help would be appreciated. Thanks,
Brett

---

### Post by monkeyking on 2008-12-31
did your soundcard work before your upgrade?

---

### Post by SonnHalter on 2008-12-31
> **monkeyking said:**
> did your soundcard work before your upgrade? 

he just said it did. Can you find a linux driver for your comp online maybe?

---

### Post by baddison on 2008-12-31
If I could just find a way to start the x-server then maybe I could fix the problem but the problem is preventing ubuntu from starting the x-server in the first place.  I have tried to boot in recovery mode to fix the x-server with no luck.  I even did a check to see if any packages were broken but did not find any.  If anyone knows of a command to start the x-server to get into the gui when the x-server doesn't start during boot up that would be great.  I don't know if I already stated this but my laptop is a Compaq presario X6000 with an ati x600 video card.
Thanks and happy new years to everyone!

---

