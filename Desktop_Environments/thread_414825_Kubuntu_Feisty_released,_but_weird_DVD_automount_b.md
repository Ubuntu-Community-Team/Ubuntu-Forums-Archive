---
title: "Kubuntu Feisty released, but weird DVD automount bug still present..."
date: 2007-04-20
forum: Desktop Environments
---

### Post by gatewayasteroid on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95868](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95868) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See here:

[http://ubuntuforums.org/showpost.php?p=2362598&postcount=3](http://ubuntuforums.org/showpost.php?p=2362598&postcount=3)

As I said it's a very annoying bug, even if it seems to affect only a minority of DVDRW devices.

What can we do for asking to incorporate the (working) Debian Etch patch into the Feisty hal package?

~

For the moment, a quick workaround:

just extract the attached file into /etc/hal/fdi/policy to fully disable the CD/DVD automount feature.

Then you can just [http://ubuntuforums.org/showpost.php?p=2362681&postcount=5](http://ubuntuforums.org/showpost.php?p=2362681&postcount=5)

Hope it helps

bye

---

### Post by encho on 2007-04-20
It is annoying, hope they'll fix it soon. I'm kinda disappointed as well to see such a bug coming into final release.

We need more work from kubuntu devs, to catchup with the ubuntu bling. Where's easy codec installation in kubuntu, where are the new features, where is... ok, maybe an issue for another thread.

Thanks for the fix though.

---

### Post by gatewayasteroid on 2007-05-13
FYI

Pardus Linux [http://www.pardus.org.tr/eng/](http://www.pardus.org.tr/eng/) development team fixed this bug in a few days:

[http://bugs.pardus.org.tr/show_bug.cgi?id=5633](http://bugs.pardus.org.tr/show_bug.cgi?id=5633)

---

### Post by beckejc on 2007-06-26
I have this exact issue in Xubuntu Feisty as well.  DVD works great with programs that handle their own mount (mplayer, xine, etc.).  

Blank data DVD's will not automount when clicked on the desktop or in Thunar.

---

