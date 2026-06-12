---
title: "NDIS gtk problem"
date: 2006-03-19
forum: Desktop Environments
---

### Post by Geffers on 2006-03-19
Recently I posted a question about installing ndiswrapper, I have followed the advice offered re using synaptic but I cannot find ndisgtk.

I was initially advised it should be shown in the listing within synaptic above ndiswrapper but no luck.

Can I just search on the web for ndisgtk and download it of does it appear I have done something wrong when I installed kubuntu.

Geffers

---

### Post by fimbulvetr on 2006-03-19
If you do this:

```

$ apt-cache search ndisgtk
ndisgtk - graphical frontend for ndiswrapper (installation of Windows WiFi drivers)

```

Your result is not the same? Did the person who told you to install this run dapper and not breezy?

I'd highly recommend not installing random packages from the web. A packing system, in this case apt, should have (almost) complete control over every piece of software installed. The day you start breaking those rules, the entropy only gets worse and eventually leads to a reinstall. Thats just my experience, and I've been using linux since 97.

---

### Post by Geffers on 2006-03-19
[QUOTE=fimbulvetr]If you do this:

```

$ apt-cache search ndisgtk
ndisgtk - graphical frontend for ndiswrapper (installation of Windows WiFi drivers)

```

Your result is not the same? Did the person who told you to install this run dapper and not breezy?

I'd highly recommend not installing random packages from the web. A packing system, in this case apt, should have (almost) complete control over every piece of software installed. The day you start breaking those rules, the entropy only gets worse and eventually leads to a reinstall. Thats just my experience, and I've been using linux since 97.[/QUOTE]

I think anyway ndisgtk is a Gnome program so not sure how well or if it runs under KDE.

I've had a go using the command line following advice from a different thread.

Thanks for advice.

Geffers

---

### Post by Retrix on 2006-03-20
ndisgtk is located in the universe repositories so you'll need to have those enabled. It should run fine under KDE, but there's a dependency bug in the breezy version (its fixed in dapper). Just make sure you have python-gtk2 and python-glade2 installed as well.

-Sam

---

