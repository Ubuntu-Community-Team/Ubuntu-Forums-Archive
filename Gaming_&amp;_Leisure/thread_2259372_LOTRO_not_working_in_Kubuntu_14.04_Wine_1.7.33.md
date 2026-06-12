---
title: "LOTRO not working in Kubuntu 14.04 Wine 1.7.33"
date: 2015-01-04
forum: Gaming &amp; Leisure
---

### Post by teddybairs1 on 2015-01-04
I recently installed LOTRO under Wine 1.7.33 after reading online that it should work without issue. However, after having spent hours downloading the 19GB of files needed to actually play the game, I use the launcher it came with within wine and it hangs once it reaches the screen after the splash screen. Once it told me it was checking Akamai components, and another time it was telling me it was downloading EN LOTRO splash screen. However, it hangs at either point and won't go any further. Pylotro won't connect it either (I used the Windows installer under wine since the Linux version seems to be out of date and uninstallable under 14.04). A friend wanted me to get online with it so he could have someone to romp through Moria with. Any help would be appreciated.

---

### Post by hellogoodbye on 2015-01-08
I myself have been struggling with installing LOTRO on my Ubuntu 14.04 LTS.
 This page helped me to at least get past the issues you have been having and I've managed to get to where I can choose my char. Then it hangs up again. It may be just my system, maybe some setting I haven't figured out yet. Let me know if it helps! :)
[https://sites.google.com/a/lordoftheringsonline-wiki.com/wiki/guides/technical-guides/running-lord-of-the-rings-online-with-linux](https://sites.google.com/a/lordoftheringsonline-wiki.com/wiki/guides/technical-guides/running-lord-of-the-rings-online-with-linux)

---

### Post by teddybairs1 on 2015-01-08
I've actually been reading several posts just like this. the problem with them is that they're all two years old. The current version of WINE is 1.7.33, not 1.3, and the current version of Ubuntu is 14.10 not 12.04. The package for pyLOTRO is packaged for Precise (12.04), and you have to install python-central from the precise repo just to get it to install. I'm going to make a wild guess and say that because all the issues with LOTRO under WINE were resolved two years ago, no one has gone back and revisited it to make sure everything was still compatible with current versions. Everything I've read that's recent says that it should work out of the box, so to speak, with WINE, without pyLOTRO or installing a separate Windows folder. Thanks anyway. BTW I don't think it's just your system. I think it's for the above reason, no one has bothered maintaining compatibility. Even the appDB entry on Winehq.org is out of date.

---

