---
title: "Problem with Plasmoids and Internet Connection"
date: 2009-12-24
forum: Desktop Environments
---

### Post by FatalChaos on 2009-12-24
I've been using ubuntu for a while now but decided to give kubuntu a shot. So far things have are pretty good, but there has been one problem I've been having problems with the plasmoids that require internet connection, like google calendar, remember the milk, and the news rss feed. 

Basically, the plasmoids load before the network manager has a chance to connect to a wireless network. Instead of automatically reloading once I'm connected to a network though, the plasmoids simply freeze up. Even hitting reload doesn't seem to work, except for the google calendar one, where it reloads, but then tells me I need to enable cookies. Any ideas?

---

### Post by MooPi on 2009-12-24
It sounds as if you have them starting with your OS. Go to your applications menu>Preferences>Startup Applications , and un-check whatever is needed.

---

### Post by FatalChaos on 2009-12-24
I can't find such an option in KDE, and even then it's missing the point. I want the plasmoids (widgets) to start up with the operating system. The thing that's bothering me is that the plasmoids refuse to play nice if the internet connection is not established before the plasmoids boot up. It seems to me like if there is no internet connection, there should be a way to just make the plasmoids wait a bit instead of having them just sort of fail.

---

### Post by Zorael on 2009-12-25
Curious. I always imagined they would react to the dbus calls emitted when the connection goes up. Maybe this should be taken up at #plasma on irc.freenode.net, or field as a bug on bugs.kde.org.

At least in 4.4b2, the News widget seems to be simply broken and doesn't redraw if you hit Reload, ending up with a blank widget until you change a setting (toggle title/description/etc). Sometimes I get it to just say 'Failed to load feed', and no matter how many times I reload or change its settings it just doesn't work. If I add the same feed again, though, it works again (in duplicate). I haven't had similar issues yet with the RSSNOW widget.

---

