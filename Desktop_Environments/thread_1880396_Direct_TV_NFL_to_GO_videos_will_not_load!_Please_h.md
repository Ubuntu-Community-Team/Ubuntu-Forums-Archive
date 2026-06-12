---
title: "Direct TV NFL to GO videos will not load! Please help!!"
date: 2011-11-13
forum: Desktop Environments
---

### Post by sentinelace on 2011-11-13
I login to the direct tv site to watch the nfl games as I pay for the service.  Works on my windows box but I cannot get it to work under ubuntu.  Tried firefox and chrome.  No go.  Java and adobe flash player are installed.  Video never loads.  Am I missing a plugin?  The site says it's flash

---

### Post by sentinelace on 2011-11-16
bump, no one?

---

### Post by ubudog on 2011-11-16
Have you tried this?
```
sudo apt-get install ubuntu-restricted-extras
```
(in a terminal)

---

### Post by sentinelace on 2011-11-16
No.  What does that do exactly?

---

### Post by ubudog on 2011-11-16
It installs some codecs, and a few other things that may be required to view multimedia like that.

---

### Post by sentinelace on 2011-11-16
I'll let you know if that works sunday ;) but why wouldn't this be installed by default?

---

### Post by ubudog on 2011-11-16
> **sentinelace said:**
> I'll let you know if that works sunday ;) but why wouldn't this be installed by default?

Restricted, by some countries.  Here is some more info:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

:)

---

### Post by sentinelace on 2011-11-20
Still doesn't work :(

---

### Post by Frogs Hair on 2011-11-20
It appears they have a Mac or Windows system requirement .

---

### Post by sentinelace on 2011-11-20
> **Frogs Hair said:**
> It appears they have a Mac or Windows system requirement .

That makes no sense.  It's browser based.  What could be different?

---

### Post by sentinelace on 2011-11-24
bump.  Anyone?

---

### Post by sentinelace on 2011-12-12
It's hard to believe no one else is an NFL fan?

---

### Post by chaos_efphect on 2011-12-12
does it require sliver light?

---

### Post by sentinelace on 2011-12-12
Well it says supported On Mac so I would think not.

---

### Post by Frogs Hair on 2011-12-12
You will need to install Quicktime which is available in the Gstreamer plug-ins . The other option is Moonlight , which is Silverlight for Linux and often doesn't work due to a DRM block .

That is why they suggest MS or Mac . [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

### Post by sentinelace on 2011-12-12
If this works you are my new best friend!!

---

