---
title: "ED2K Link handler for aMule"
date: 2006-04-01
forum: Desktop Environments
---

### Post by mybuffalo on 2006-04-01
I've installed aMule through Automatix but is not able to make the ed2k link handler to work in Firefox 1.5.

I've tried the suggestion from aMule's website to add the ed2k path in the about:config, but I was not able to find the file ed2k.

I've also tried a Firefox extension - Firemule.  Also not able to get it to work.

Any help is much appreciated.

---

### Post by maitreya on 2006-04-01
[QUOTE=mybuffalo]I've installed aMule through Automatix but is not able to make the ed2k link handler to work in Firefox 1.5.

I've tried the suggestion from aMule's website to add the ed2k path in the about:config, but I was not able to find the file ed2k.

I've also tried a Firefox extension - Firemule.  Also not able to get it to work.

Any help is much appreciated.[/QUOTE]

I don't use firefox so this may not work. According to this [http://blog.ryaneby.com/archives/firefox-protocol-handlers/](http://blog.ryaneby.com/archives/firefox-protocol-handlers/), you can add protocol handlers for ed2k links.

Just go to about:config, right click and new->string. Input network.protocol-handler.app.ed2k as name and ed2k as value.

I don't think you need to add the path if your aMule is installed correctly. Try opening a terminal and typing "which ed2k" without quotes. It will show the location of the file. If it doesn't output anything the your aMule is not installed correctly. You can reinstall aMule through the universe repository.

---

### Post by mybuffalo on 2006-04-01
Thanks for the help.

I've just found a minute ago that I need to install amule-ed2k for this to work.

Problem solved.

---

