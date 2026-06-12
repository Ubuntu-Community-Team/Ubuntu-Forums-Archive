---
title: "DVD automount fix for Xfce in Gutsy?"
date: 2007-11-14
forum: Desktop Environments
---

### Post by fondfire on 2007-11-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/thunar-volman/+bug/151028](https://bugs.launchpad.net/ubuntu/+source/thunar-volman/+bug/151028) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Is the thunar-volman package going to be updated to version 0.1.2-1ubuntu4 or beyond for Gutsy?  I really miss having my DVDs properly automount!!  It's my biggest gripe since I upgraded . . .

Is there anything I can do to help make that happen?

---

### Post by m_gasior on 2007-11-15
Backport from Hardy made by me

[http://gasior.cba.pl/ubuntu/gutsy/thunar-volman_0.1.2-1ubuntu4_i386.deb]("http://gasior.cba.pl/ubuntu/gutsy/thunar-volman_0.1.2-1ubuntu4_i386.deb")

---

### Post by fondfire on 2007-12-08
Thanks, m_gasior, but that didn't really work for me, as I'm using an AMD64 version of Ubuntu.

I did find something that works, though!  I went to [http://archive.ubuntu.com/](http://archive.ubuntu.com/) and downloaded the following three packages:

  [http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.10-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.10-2ubuntu3_amd64.deb)
  [http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.10-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.10-2ubuntu3_amd64.deb)
  [http://archive.ubuntu.com/ubuntu/pool/main/t/thunar-volman/thunar-volman_0.1.2-1ubuntu4_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thunar-volman/thunar-volman_0.1.2-1ubuntu4_amd64.deb)

I installed those three packages using the command:

  sudo dpkg -i libhal-storage1_0.5.10-2ubuntu3_amd64.deb \
    libhal1_0.5.10-2ubuntu3_amd64.deb \
    thunar-volman_0.1.2-1ubuntu4_amd64.deb

And that worked!  My DVDs play as soon as I pop them into the computer now, which is a feature I very much enjoy!!!

:KS  :guitar:  :KS

Hope this helps somebody.

--Fondfire

---

