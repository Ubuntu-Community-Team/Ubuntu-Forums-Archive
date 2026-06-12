---
title: "Epiphany flash"
date: 2012-07-24
forum: Desktop Environments
---

### Post by degarb on 2012-07-24
I installed Epiphany, Epiphany-webkit, mozplugger.  Got usr/lib/mozilla/plugins with flash there.

Midori and FF and Opera have flash.  But I cannot use Epiphany, cause the flash isn't working.

---

### Post by orange2k on 2012-07-25
Do the following:

```
sudo dpkg-reconfigure flashplugin-installer
```

---

### Post by degarb on 2012-07-25
That sudo command - typical - wiped out flash for all my browsers.  Opera and midori now have no flash.

I tried downloading gz too.   No luck.

Need better solution. or clarification.

---

### Post by degarb on 2012-07-25
synaptic>flashplugin>reinstall got Opera and midori flash back, but not epiphany.

---

### Post by orange2k on 2012-07-25
> **degarb said:**
> synaptic>flashplugin>reinstall got Opera and midori flash back, but not epiphany.

Well, that command worked for me. I also had no flash in Epiphany.

Did a message with a question pop up when you ran that command asking you something about downloading flash?

---

### Post by degarb on 2012-07-25
> **orange2k said:**
> Well, that command worked for me. I also had no flash in Epiphany.

Did a message with a question pop up when you ran that command asking you something about downloading flash?

yes, it said just hit enter and it would download it for me.  Which is the way it should be.  But this didn't work.  So, I went to get.flash.adobe or such and downloaded some gz file. Pointed to it.  And still, no luck.

After both attempts, the flash was killed from at least Opera and Midori.  Reinstalling from synaptic at least fixed Opera and Midori.

---

### Post by vasa1 on 2012-07-25
One of the reasons I stay away from "Epiphany", now called Web, is that, the last time I looked, you don't get the latest version from the USC. The more important reason is that there doesn't seem to be much "support" available as you may be discovering.

---

### Post by degarb on 2012-07-26
> **vasa1 said:**
> One of the reasons I stay away from "Epiphany", now called Web, is that, the last time I looked, you don't get the latest version from the USC. The more important reason is that there doesn't seem to be much "support" available as you may be discovering.

Hmm.  I have a 2003 6 gig hd laptop, 1 gig ram, and Probably 800 ghz, in living room for kid games, streaming movies, streaming radio, OpenOffic writer, and browsing.  It is running Ubuntu 9, took a while to setup in early 2010.  Opera auto-updated and hopelessly broke, Firefox is too slow, Chrome's cache is nearly unsuppressed, and never could get Midori installed on it.  Fortunately, Epiphany and its flash (for kid games on pbs.org, etc) works.

I wonder if I just need to find a better deb for Epiphany for this P4 2ghz machine.  I think I just used synaptic.

Fortunately, Epiphany, here, is not critical, as it is on the Entertainment center computer.

---

