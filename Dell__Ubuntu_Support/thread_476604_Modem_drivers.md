---
title: "Modem drivers?"
date: 2007-06-17
forum: Dell  Ubuntu Support
---

### Post by teddybairs1 on 2007-06-17
Anyone know where to get the conexant modem drivers for the laptop?

---

### Post by HotShotDJ on 2007-06-17
Had you searched the forum for the word "conexant" you would have found this:
> Just got off the phone with the Linux people at Dell using that number. What a breath of fresh air to be talking to somebody that didn't keep saying "we don't support Linux" -- As per that call, the drivers are packaged and ready but there is some "paperwork" (regarding the third-party license, no doubt, although he didn't say specifically) that needs to be done before it can be publicly released. He said 1 - 2 weeks. Lets hope! 

---

### Post by neptho on 2007-06-17
Keep in mind that with the onboard Intel HD Audio, the Conexant drivers do replace key bits of that driver, so if you upgrade ALSA, you'll likely kill your modem.

---

### Post by HotShotDJ on 2007-06-17
> **neptho said:**
> Keep in mind that with the onboard Intel HD Audio, the Conexant drivers do replace key bits of that driver, so if you upgrade ALSA, you'll likely kill your modem.That IS theoretically possible.  I tested your hyptothesis using the crippled hsfmodem drivers from Linuxant -- Since I've applied all updates to my Feisty system, if some upgrade to ALSA killed the OP's modem [driver], then I should be unable to use my modem as well.  As it turned out, that is not the case.  My Conexant modem continues to function (albeit slowly and with out fax support due to crippled driver).

Neptho -- your hypothesis was actually a good one, it just didn't withstand my test. :)  My testing, however, was imperfect.  If an upgrade with the potential of disabling the hsfmodem driver was applied PRIOR to my installing hsfmodem, then I would not have detected the problem with this test.  HOWEVER, even if that is true, it suggests that reinstalling hsfmodem would correct the problem you suggest.  Of course, the OP's inability to obtain the driver at this time precludes testing this.

---

### Post by teddybairs1 on 2007-06-17
HotshotDJ - Thanks. But the sarcasm wasn't necessary. I just asked a question.

---

### Post by neptho on 2007-06-17
> **HotShotDJ said:**
> Neptho -- your hypothesis was actually a good one, it just didn't withstand my test. :)  My testing, however, was imperfect.  If an upgrade with the potential of disabling the hsfmodem driver was applied PRIOR to my installing hsfmodem, then I would not have detected the problem with this test.  HOWEVER, even if that is true, it suggests that reinstalling hsfmodem would correct the problem you suggest.  Of course, the OP's inability to obtain the driver at this time precludes testing this.

I've witnessed this in Debian, before.

 f you keep the packages, and are able to have the developer tools (who doesn't?) available to recompile, and reinstall the audio driver, you will get your modem back, but the sound, AFAIK is still crippled.  I've never been able to make those bundled hfsmodem drivers work with duplex mode, or dmix software mixing (I believe they use an earlier source fork).

The hsf driver package should be kept available on the system for any update; even minor kernel updates may tickle it, depending on how the modules have been signed, and how the kernel mapping may change due to architectural changes, however with the new -generic kernel modularization, this is fairly unlikely, so, yeah.

---

### Post by highlighter on 2007-06-17
If you have a real DellBuntu laptop, I suggest to call dell. They have the driver for this modem.

---

### Post by HotShotDJ on 2007-06-17
> **teddybairs1 said:**
>  But the sarcasm wasn't necessary.Sarcasm wasn't the intent.  I was just showing you how you could have gotten your answer faster, while also answering your question.  If that wasn't appreciated, then I'll give you your money back ;).

---

