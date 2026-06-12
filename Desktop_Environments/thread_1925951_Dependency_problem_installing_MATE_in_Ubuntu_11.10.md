---
title: "Dependency problem installing MATE in Ubuntu 11.10"
date: 2012-02-15
forum: Desktop Environments
---

### Post by Ardghal on 2012-02-15
I'm trying to install MATE through this tutorial:

[http://ubuntuguide.net/ubuntu-11-10-install-classic-gnome2-desktop-linux-mint-mate](http://ubuntuguide.net/ubuntu-11-10-install-classic-gnome2-desktop-linux-mint-mate)

But when I try installing **mint gnome shell extension** throught the Software Center, I get an error saying it depends on [FONT="Courier New"]gnome-core[/FONT], but it won't be installed.
So I install [FONT="Courier New"]gnome-core[/FONT] through Synaptic, then try again in Software Center, but it shows the same error.
Then I try to install the package [FONT="Courier New"]gnome[/FONT] through Synaptic, but it says it depends on [FONT="Courier New"]epiphany-extensions[/FONT] and it won't install.
Finally I try to install [FONT="Courier New"]epiphany-extensions[/FONT] and it says that it needs [FONT="Courier New"]epiphany-browser (<3.1)[/FONT], but will install [FONT="Courier New"]3.2.1-2ubuntu1~oneiric1[/FONT]. And it doesn't let me do anything else.

To sum up: it *seems* I need an older [FONT="Courier New"]epiphany-browser[/FONT] package. The current packages are Gnome 3.2, I believe. If I'm right, where could I get the older packages? Otherwise, what else could I do to install the MATE packages?

---

### Post by Rodney9 on 2012-02-15
Seems al lot of people are having problems.

May be best to try [Mint]("http://linuxmint.com/rel_lisa_whatsnew.php") itself.

or read through this, page 25 has a re-spin you could try - 

[http://ubuntuforums.org/showthread.php?t=1858282&highlight=mate](http://ubuntuforums.org/showthread.php?t=1858282&highlight=mate)

Rodney

---

### Post by bluexrider on 2012-02-15
> **Ardghal said:**
> I'm trying to install MATE through this tutorial:

[http://ubuntuguide.net/ubuntu-11-10-install-classic-gnome2-desktop-linux-mint-mate](http://ubuntuguide.net/ubuntu-11-10-install-classic-gnome2-desktop-linux-mint-mate)

But when I try installing **mint gnome shell extension** throught the Software Center, I get an error saying it depends on [FONT=Courier New]gnome-core[/FONT], but it won't be installed.
So I install [FONT=Courier New]gnome-core[/FONT] through Synaptic, then try again in Software Center, but it shows the same error.
Then I try to install the package [FONT=Courier New]gnome[/FONT] through Synaptic, but it says it depends on [FONT=Courier New]epiphany-extensions[/FONT] and it won't install.
Finally I try to install [FONT=Courier New]epiphany-extensions[/FONT] and it says that it needs [FONT=Courier New]epiphany-browser (<3.1)[/FONT], but will install [FONT=Courier New]3.2.1-2ubuntu1~oneiric1[/FONT]. And it doesn't let me do anything else.

To sum up: it *seems* I need an older [FONT=Courier New]epiphany-browser[/FONT] package. The current packages are Gnome 3.2, I believe. If I'm right, where could I get the older packages? Otherwise, what else could I do to install the MATE packages?


Don't do it. Just get a fresh DVD and download and burn, burn, burn. Do a fresh install. It's not worth the hassle, REALLY.

---

### Post by Ardghal on 2012-02-16
> **Rodney9 said:**
> Seems al lot of people are having problems.

May be best to try [Mint]("http://linuxmint.com/rel_lisa_whatsnew.php") itself.

or read through this, page 25 has a re-spin you could try - 

[http://ubuntuforums.org/showthread.php?t=1858282&highlight=mate](http://ubuntuforums.org/showthread.php?t=1858282&highlight=mate)

Rodney

Thanks for replying, but I'd rather make MATE work in this installation of Ubuntu. I tried the new Mint in VirtualBox and it was great; but I had issues getting the internet connection to work as intended in Ubuntu, so I really don't want to mess with that again. It's the only thing keeping me from Mint, but it's a big deal.

Thanks for the link to the MATE thread, though. I hadn't seen it. :) Maybe I'll find something there.

[QUOTE=bluexrider]
Don't do it. Just get a fresh DVD and download and burn, burn, burn. Do a fresh install. It's not worth the hassle, REALLY. [/QUOTE]

I understand it's a bad idea to start tampering with dependencies. I've seen it go bad before, but I'm really tired of GNOME3's fallback mode being a sad replacement for a DE that worked. I'm willing to try, at least. :D

**UPDATE:**

OK, I solved it in a different way. This question in [askubuntu.com]("askubuntu.com"), [http://askubuntu.com/questions/87040/how-to-install-mate-in-11-10-and-above](http://askubuntu.com/questions/87040/how-to-install-mate-in-11-10-and-above) has a method that worked perfectly. It's a different repository that has no conflict with any existing packages. I'm using MATE right now. It works. :D

---

