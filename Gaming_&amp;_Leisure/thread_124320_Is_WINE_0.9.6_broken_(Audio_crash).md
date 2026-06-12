---
title: "Is WINE 0.9.6 broken (Audio crash)"
date: 2006-02-01
forum: Gaming &amp; Leisure
---

### Post by mulperi on 2006-02-01
I have working ALSA as far as i know but winecfg always crashes when I click the "Audio" tab. 

Have tried an older Wine found in the backports repostory. It did not crash but OSS sound did not work. However I was able to play some games without sound.

Question is if Wine 0.9.6 is really broken or is my Ubuntu somehow wrongly configured. 

Could someone with a working Wine 0.9.6 tellme what ALSA setting you have?

Please

---

### Post by Kuprin on 2006-02-01
I'll give it a go later today and see what I get for ya. :)

---

### Post by mulperi on 2006-02-01
Thanks man... i'm sure there are several of us who just can't get sound working.

---

### Post by polpak on 2006-02-01
It's been broken since 9.3 AFAIK.

Here's the bugzilla info:

[http://bugs.winehq.org/show_bug.cgi?id=4051](http://bugs.winehq.org/show_bug.cgi?id=4051)

It's fixed in CVS, and should work fine in the next release.

---

### Post by mulperi on 2006-02-01
Thanks Polpak, this was what I expected but could not find googling.

The problem with this kind of bugs is that you end up meesing with your settings so much that system breaks down for good. Now I can only wait for next release because one thing I want to avoid is installing windows again :-)

---

### Post by mulperi on 2006-02-03
winehq packet manager said there was a new version available. This new one does not crash when configuring audio in winecfg, but still I have some problems in my alsa settings because it complains about 2 channels needed... even turning sound completely off crashes with directx sound.

go figure

---

### Post by Perfect Storm on 2006-02-04
wine 0.9.7 is now avaible, peraps they fixed the issue.

---

### Post by magnusbb on 2006-02-04
I can confirm that 0.9.7 fixes the issue.

---

