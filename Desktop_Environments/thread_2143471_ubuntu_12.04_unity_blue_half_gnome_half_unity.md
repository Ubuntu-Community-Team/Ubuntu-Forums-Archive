---
title: "ubuntu 12.04 unity blue half gnome half unity"
date: 2013-05-09
forum: Desktop Environments
---

### Post by Vi Kingske on 2013-05-09
**h**ello,

yesterday, after playing the arcade game powermanga, I had to note that  my upper panel of my ubuntu 12.04 went blue, that the icons changed  (gnome like, as far as I know it, I'm a newbie) also, icons weren't  visible anymore from the panel where you start programs. also, if I open  pcmanfm, nautilus, thunderbird, many things have changed, and  everything is blue :-(( 

when I open an guest session, everything is normal. weird isn't it? I  tried reinstalling unity, compiz, but it didn't help a thing.

could anyone help me with this problem? I'm quite a newbie, so it would  take me a lot of time and effort to set up a new account.

thanks in advance!!

---

### Post by Vi Kingske on 2013-05-09
I did following thing and my unity is acting normal again, wouhouw!

> "Try to do this:

    Login into Ubuntu
    Open a terminal by hitting CTRL + ALT + T

    Insert and run this commands:

    gconftool-2 --recursive-unset /apps/compiz-1
    unity --reset

    Restart, this should work."
[http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration)
How do I reset my Unity configuration? - Ask Ubuntu
Thu May 09 2013 14:36:32 GMT+0200 (CEST)

---

