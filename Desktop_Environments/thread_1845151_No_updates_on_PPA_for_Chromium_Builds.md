---
title: "No updates on PPA for Chromium Builds"
date: 2011-09-16
forum: Desktop Environments
---

### Post by kmand on 2011-09-16
The PPA Chromium builds for Ubuntu at

    [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

stopped updating 12 days ago. Is there a new site?

---

### Post by Frogs Hair on 2011-09-16
I use Firefox nightly builds and there have been times when updates come everyday and other times when I go without updates for varying  periods of time . I wouldn't worry about it , the project is likely alive and well . If the software source starts to fail to connect during updates then you might want to find out if the project is still  active.

---

### Post by chronniff on 2011-09-26
I have been curious about this too, the chromium ppa has always been good about always keeping up to date, but now I see that the daily ppa has been idle for the past 3 weeks....I use the dev channel, and I have had to switch over to the official chrome dev builds from googles repo, which takes forever to check everytime I do an apt-get update.  Plus I generally like the idea of having the open source project builds, for a lot of reasons, although none that really have any significant impact on the way I use the browser

---

### Post by Frogs Hair on 2011-09-26
It was reported in another thread that there is a manpower shortage on that project but it is still active .

---

### Post by r1ft on 2011-09-29
They should at least put up a notice on the LP project page. I sent Fabien Tassin a message from LP for a status update; I will update here if he replies.

---

### Post by forcecore on 2011-10-06
Any news? i did not find any other ppa?

---

### Post by hugmenot on 2011-10-06
FTA seems to be AWOL, so I got his build scripts from launchpad and built 16.0.899.0. It woks smoothly but takes quite some time to pull and bundle up the source tree. 

But since I applied an extra patch that makes Ctrl-N open a new tab, not a window, you probably don’t want my build.

---

### Post by forcecore on 2011-10-07
Strage is why even official Ubuntu repo still has v13 not 14?

---

### Post by Krytarik on 2011-10-07
> **forcecore said:**
> Strage is why even official Ubuntu repo still has v13 not 14?
You mean v12, respectively v14 for Oneiric 11.10!? :P

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=chromium-browser](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=chromium-browser)

---

### Post by forcecore on 2011-10-08
> **Krytarik said:**
> You mean v12, respectively v14 for Oneiric 11.10!? :P

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=chromium-browser](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=chromium-browser)

finally, thanks. Some day ago i checked and there still was v13 but now finally v14 arrived. Strange is that when chromium ppa got build then official got too? are official repo dependant on Chromium ppa?

---

### Post by Krytarik on 2011-10-08
> **forcecore said:**
> Strange is that when chromium ppa got build then official got too? are official repo dependant on Chromium ppa?
Not really, reg. both. Typically, this kind of PPAs are ahead of the official repos; in this case (even though people are complaining) the PPA provides v15 - since more than one month - , while the most recent version of all official repos is v14, as you just learned.

And no, PPAs and official repos are not per-se depending on each other, although there might be some kind of interconnection in some cases, specifically in terms of the maintainer and, therefore, release dates.

---

### Post by r1ft on 2012-02-09
It seems the PPA is dead again; no updates for 5 weeks now! Does anyone know why?

---

### Post by Krytarik on 2012-02-09
> **r1ft said:**
> It seems the PPA is dead again; no updates for 5 weeks now! Does anyone know why?
You could ask the maintainer himself, if you are that inclined ;-) ; pulled from the changelog file of the last package:
>  -- Chris Coulson <chrisccoulson@chinstrap.canonical.com> Thu, 05 Jan 2012 06:00:08 +0000
Regards.

---

### Post by Placenta Juan on 2012-03-05
So, any word from the developer? Or has anyone even tried contacting him?

---

### Post by rabla on 2012-03-06
Any alternatives to this ppa? 

[http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel) is the same?

---

### Post by Krytarik on 2012-03-06
> **rabla said:**
> Any alternatives to this ppa? 

[http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel) is the same?
Nope, that's for Chrome; they like to mix that up. :P

---

### Post by cmike on 2012-03-09
Any news?

---

### Post by hugmenot on 2012-03-09
> **cmike said:**
> Any news?

If you are okay with a [few customized shortcuts (Ctrl-N &#8594; New Tab, etc)](http://paste.ubuntu.com/876135/), you can get Chromi 19.0.1061 from [this PPA](https://launchpad.net/~towolf/+archive/crack/+packages)

---

