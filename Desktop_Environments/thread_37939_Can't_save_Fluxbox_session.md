---
title: "Can't save Fluxbox session"
date: 2005-05-29
forum: Desktop Environments
---

### Post by Psquared on 2005-05-29
I've got Fluxbox up and running and I really like it. However, to make it complete I need a couple of things.

First, I need to know how to save a Fluxbox session so it will start like I left it. Specifically, I want gdesklets to start automatically.

Second, I want to be able to run Gnomebaker in Fluxbox. It's not in the menu, but I know how to add it if I knew the command. If I type gnomebaker in a terminal nothing happens. Will it work in Fluxbox?

Third, (a common problem I know) if my wireless connection gets dropped I have to go into Gnome to restart it. What is the command for wireless or network configuration settings? Is it something like system-network-config???

One last question. Will Blackbox stuff work in Fluxbox? There are all kinds of little addons for Blackbox like bbmail, etc. I would like to use those if I can.

Thanks.

---

### Post by Moobert on 2005-05-29
your going to need to make a startup script:

The method from the fluxbox site will clash with gdm unless you use .xsession iirc.

[http://fluxbox.sourceforge.net/docbook/en/html/app-setup.html](http://fluxbox.sourceforge.net/docbook/en/html/app-setup.html)

I myself did it a different way, to start with I added this line to ~/.fluxbox/init

```

session.screen0.rootCommand: ~/.fluxbox/startapp

```

in the session.screen0. section.

then I created the startapp script to load all my apps on startup eg

```

#!/bin/sh

fbsetbg -l &

ps -ef | grep torsmo | awk '{ print $2 }' | xargs kill
torsmo &

```

'ps -ef | grep torsmo | awk '{ print $2 }' | xargs kill' scans to see if torsmo is aready loaded and if so.. kills it.

As for the blackbox stuff it should work fine as fluxbox comes from the blackbox code.

---

