---
title: "disabling nolisten tcp in 11.04 gdm/X"
date: 2011-05-10
forum: Desktop Environments
---

### Post by melric on 2011-05-10
I upgraded a working Ubuntu system that I'd previously configured to accept tcp connections for the X server, which it's magically gone and added back in again. I can't now figure out how to disable it.

I've edited /etc/gdm/gdm.schemas and changed DisallowTCP to false. I've edited /etc/X11/xinit/xserverrc and removed the nolisten tcp line, but it still comes up with it.

The System->Administration->Login Screen has no option for security (pretty sure that's how I fixed it last time).

Any pointers would be greatly appreciated.

---

### Post by jmaccelari on 2011-05-11
I've also tried this (unsuccessfully) and also removed the "-nolisten tcp"option to X in /etc/X11/xinit/xserverrc, restarted the service and also re-frikkin'-booted and still get: /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-4EGA78/database -nolisten tcp vt7  I can't use the ssh -X trick as I have to run apps off old Solaris servers that don't support it...

---

### Post by jmaccelari on 2011-05-11
Sheez - there's a copy of gdm.schemas in /usr/share/gdm and this is the one it uses.  Now working.  This must be a bug...

---

### Post by melric on 2011-05-12
That fixed it for me too. Cheers!

---

### Post by fmouse on 2011-07-01
<rant>
Sheesh!!!  I'm configuring a virgin install of Ubuntu 11.04.  I thought Linux was about choice.  There's no config option for this.  There's not even a gnome help file for en_US for gdm that talks about this!

Yes, this solution fixed the problem for me, too (thanks!) and I *depend* on being able run rxvt on servers and have the display show up on boxes on my private, RFC1918 network, accessible via VPN.

This is CRAP!  I'm sorry to say it, but Canonical Partners is trying to out-Microsoft Microsoft when it comes to hiding stuff so as to protect us from ourselves.  I started using X and appreciating the advantages of X back when Linux was at version 1.x.x, back in the 1990s.  Unix, and by extension, Unix-derived OSes such as Linux are very powerful, and if you take reasonable care, very secure.  I came to appreciate many of these advantages, and so I'm still using a Unix-based OS today for all my work, 17 years later.  Now it seems we're being fed a lot of pablum and treated like children.

What's next?  Will they redesign filesystem so as to nuke Unix permissions and ownership?  How about NTFS-lite?  Damn!  :(
</rant>

---

### Post by fmouse on 2011-07-01
Sorry, folks, but I've been working with Open Source software since the early 1980's, before "Open Source" was even a publicly acknowledge concept, thanks to the likes of Eric Raymond and Richard Stallman.  I'm nearly 70 years old.  Tell me to buzz off and go take my meds if you wish, but I still work as a Linux consultant and my opinions and insight are good enough to make the cut on numerous Linux technical forums.

---

### Post by basilarchia on 2011-09-10
fmouse: You are totally correct. WTF is going on over at ubuntu? It's turned into a total disaster. The only thing they did right was the installer. Great installer & upgrade process. But, what is being installed is totally ruining it.

---

### Post by rknize on 2012-02-16
Since this thread still comes up at the top of Google results and the information in here is stale for Oneiric (which no longer uses gdm), here is what you need to do:

As root (or sudo), edit /etc/lightdm/lightdm.conf and add the following two lines under "SeatDefaults" (the latter is a security precaution):

[SeatDefaults]
...
xserver-allow-tcp=true
allow-guest=false

---

### Post by maloo on 2012-02-28
I know this is old and ubuntu has moved away from gdm but just wanted to point to this thread which looks like a better solution:
[http://ubuntuforums.org/showthread.php?t=1642286]("http://ubuntuforums.org/showthread.php?t=1642286")

> Create a new file /etc/gdm/custom.conf with this content:

Code:
```
[security]
DisallowTCP=false
```
Then reboot.

---

