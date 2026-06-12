---
title: "can't use slim"
date: 2015-03-30
forum: Desktop Environments
---

### Post by mandar2 on 2015-03-30
I followed instructions from some of the available sites which tell how to use slim. It needs changing lines in _**/etc/slim.conf**_ and also creating [U][B]~/.xinititrc.
[/B][/U]
However, it constantly gives me black screen.

```

#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)


# invoke global X session script
#. /etc/X11/Xsession


case "$1" in
    openbox) exec openbox-session ;;
    unity  ) exec unity;;
esac



```

is current file.

But when i have
```

#!/bin/sh
exec openbox-session 
```

then slim blinks in only once and then ubuntu logging screen turns on with dots turning red.

Help please :(

---

### Post by Vladlenin5000 on 2015-03-30
Do you mean Simple Login Manager?
If so, don't:

[http://askubuntu.com/questions/80004/is-slim-simple-login-manager-compatible-with-11-10](http://askubuntu.com/questions/80004/is-slim-simple-login-manager-compatible-with-11-10)

---

### Post by v3.xx on 2015-03-30
Looks to be maintained to me.

[http://packages.ubuntu.com/trusty/slim](http://packages.ubuntu.com/trusty/slim)

[https://launchpad.net/ubuntu/+source/slim](https://launchpad.net/ubuntu/+source/slim)

I haven't played with slim in a while, but ~/.xinitrc was what worked for me.

After that I summarize that slim was not necessary (no DM at all) and better to just use startx.  Which can be configured in a number of ways.

[https://wiki.archlinux.org/index.php/Xinitrc](https://wiki.archlinux.org/index.php/Xinitrc)

[https://wiki.archlinux.org/index.php/xorg](https://wiki.archlinux.org/index.php/xorg)

---

### Post by mandar2 on 2015-04-01
I was trying to build an Ubuntu 14.04 LTS with openbox. However, it could not accept SLIM i dont know why. I did fresh install. I did accept SLiM instead of LightDM and once i installed the updates it screwed up. Started showing dumb blank screen. I fade up i decided to remove everything of Unity. I ran removal command with autoremove by consulting some "guides" from webpages, and autoremove later removed everything important as well. Ended up by doing fresh install of Xubuntu. 520mb Ram usage on idle. Fine.

---

