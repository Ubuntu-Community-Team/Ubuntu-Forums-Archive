---
title: "Xine and Firefox? Anyone know how?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by smoshe on 2005-12-14
Hey guys,

Firefox for some reason is defaulting to Totem for videos online. Don't know why they chose Totem for this, it doesn't seem to be able to play much of anything. Just an opinion, I absolutely hate the program. I would like to configure my firefox browser to default to Xine for these video formats, as it works with little or no configuration on my part. It would be nice if I could do it globally, but I'm willing to do it per user if I have to. I currently have six users on my (now windows free) Ubuntu network.

Anyone out there in Linux land know how to do this?

On a related note:
Seems more and more sites are using WMV format for video these days. I understand some of it is encrypted, and I'm not hoping to play that stuff. Luckily, it seems the bulk of it isn't, and my aunt (a fresh new Ubuntu Linux user) doesn't understand why this is an issue. I found the DLL for it, and Xine documentation says it's compatable (something about a abstraction layer of some sort, I gather), I tried a couple of obvious spots, but no luck. I'm not sure where to put it in my file system in order to get this to work. Any ideas on that?

I appreciate the help.

Thanks again.

---

### Post by kaamos on 2005-12-14
Try looking into a program called mozplugger. It's available in the repos.. Also mplayer and mozilla-mplayer could serve you well.

---

### Post by Raoul Duke on 2005-12-14
1. Replace Totem with Totem-xine using apt or synaptic
2. Get the required codecs from mplayer website
3. Get Mozplugger, configure /etc/mozpluggerrc to use totem, and NOT totem mozilla plugin, to play all media, or else leave mozpluggerrc as is and use mplayer for all multimedia.

---

### Post by linkunderscore on 2005-12-14
[QUOTE=Raoul Duke]
3. Get Mozplugger, *configure /etc/mozpluggerrc to use totem,* and NOT totem mozilla plugin, to play all media, or else leave mozpluggerrc as is and use mplayer for all multimedia.[/QUOTE]

how do I do that? What do I change?

---

