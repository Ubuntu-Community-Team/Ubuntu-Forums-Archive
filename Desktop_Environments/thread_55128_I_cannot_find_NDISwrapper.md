---
title: "I cannot find NDISwrapper"
date: 2005-08-07
forum: Desktop Environments
---

### Post by Maximus_Magni on 2005-08-07
I am trying to get NDISwrapper on my machine, and I cannot find it. I have tried using <sudo apt-get install ndiswrapper>, I have tried using synaptic and searching for ndis, and i even added the line <deb [http://ndiswrapper.sourceforge.net/debian](http://ndiswrapper.sourceforge.net/debian) ./> to my sources.list file, and then trying apt-get and searching in synaptic. Nothing seems to work.

---

### Post by Takis on 2005-08-07
Howdy!

Firstly, let me advise you strongly *against* including Debian repositories for an Ubuntu computer. Things may/will break. Next I have to tell you that ndiswrapper does not yet exist properly on the Ubuntu repositories.

You are by far better off downloading the source and compiling that. There are comprehensive instructions in the forums (under HOW-TOs) and on the internet, such as [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation).

If you need a bit of help, don't hesitate to post.

---

### Post by elsewhere on 2005-08-07
Actually, I'm pretty sure Ubuntu does come with the ndiswrapper module included with the standard kernel, but you will need to install the *ndiswrapper-utils* from the standard repos. This package will give you the actual userspace utilities to configure it from the command line.

Worked like a charm for me.

Hope this helps...

Cheers,
KV

---

### Post by Maximus_Magni on 2005-08-08
[QUOTE=elsewhere]Actually, I'm pretty sure Ubuntu does come with the ndiswrapper module included with the standard kernel, but you will need to install the *ndiswrapper-utils* from the standard repos. This package will give you the actual userspace utilities to configure it from the command line.

Worked like a charm for me.

Hope this helps...

Cheers,
KV[/QUOTE]
 I did the standard install of Kubuntu, and it wasn't there. Also, I keep forgeting to mention that I am using the x86-64 version of the distro. That seems to make a difference. As far as not including debian repositories, I had no clue. I thought that since K/Ubuntu were based off Debian, that it would be a good idea. Should I not try and install .deb files as well.

---

### Post by elsewhere on 2005-08-08
Ahhh, that may change things.  I'm not familiar with AMD64 setups.

If it's not showing up as being available in synpatic for your architecture then you may be best off to compile it as per Takis' post.  It should be straight forward compile, I actually did it myself the first time I installed Kubuntu because I didn't realize it was already available.  Don't remember running into any issues, but then I'm on i686.  May want to take a look at the wiki on the ndiswrapper sourceforge page  for any issues or hints.

Cheers,
KV

---

### Post by Takis on 2005-08-09
[QUOTE=Maximus_Magni]As far as not including debian repositories, I had no clue. I thought that since K/Ubuntu were based off Debian, that it would be a good idea. Should I not try and install .deb files as well.[/QUOTE]
I'd strongly advise against using .deb files unless they've been explicitly marked as for Ubuntu (very rare!).

A good analogy is like trying to put a standard kind of car part (e.g. an alternator) from Toyota into a Mitsubishi. It may fit, but chances are it plugs into the wrong places, requires features that aren't there and has features that won't be used. It MAY work, but it may also break your whole system. Avoid taking the chance, compile the programs yourself.

Okeydizzle you can compile ndiswrapper on x64 just fine, but it's generally drivers that become the real PITA. Are you using a Broadcom-based WLAN card (e.g. Asus, Belkin, Buffalo, Linksys, Microsoft, Sitecom, etc)? I put up a little FYI when I found 64-bit drivers for this.
[http://www.ubuntuforums.org/showthread.php?t=50386](http://www.ubuntuforums.org/showthread.php?t=50386)

---

