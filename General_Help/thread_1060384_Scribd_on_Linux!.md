---
title: "Scribd on Linux!"
date: 2009-02-04
forum: General Help
---

### Post by sondosia on 2009-02-04
Does anybody know why Scribd (and iPaper) don't work on Ubuntu (or, from what I've heard, any distro)? I'd really appreciate some help here...

---

### Post by icheyne on 2009-02-05
According to [Wikipedia]("http://en.wikipedia.org/wiki/IPaper"), iPaper should work on Linux as it is built with Flash. You probably have a problem with Flash.

Try installing Adobe's version - [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by sondosia on 2009-02-05
You're probably right; I've always had problems with Flash on my system despite numerous attempts to install and reinstall it. I followed the instructions in the link you sent, but when I tried to install the package adobe-flashplugin, it told me that I already have the most recent version. Any ideas on what to do next?

---

### Post by icheyne on 2009-02-05
Try Adobe's version - [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

If that doesn't work, you might as well try the new alpha version - [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

### Post by dugh on 2009-03-31
I have the latest flash 10 installed, and scribd doesn't work.  Never has.

I have no clue why people even use that pos site.

---

### Post by aml1648 on 2009-04-20
Scribd does work for me (Jaunty Beta with Firefox 3.08). I have no problem uploading files to scribd or read/comment on the documents there in small screen.

However, I cannot download files or toggle full screen as I could with Windows.

---

### Post by aml1648 on 2009-04-20
I meant Firefox 3.08. Not sure where did the funny face come from.

---

### Post by ningenity on 2009-04-27
I've been using Ubuntu for a couple of days, and ran into the same problem: Scribd's iPaper did not work.

This fixed it for me at least... hope it helps at all...

First I grabbed the Shockwave Flash installer (the Ubuntu .deb file) from Adobe and installed the latest version, 10.something.  Restarted the browser, and scribd still did not work.  Browsing about:plugins showed a different flash player version installed.  This  turned out to be swfdec-mozilla.

I removed swfdec-mozilla through the Ubuntu menus:  System -> Administration -> Synaptic Package Manager, then restarted Firefox again.

About:plugins now reports the Adobe version (10.x).  I did not have to reinstall it.  The scribd iPaper now displays fine.

The Download button above them does not work, but that's probably a separate issue.

---

### Post by everettattebury on 2009-05-01
I filed a [_support request_]("http://support.scribd.com/requests/7838") with scribd, they're working on it.

---

### Post by Norfeldt on 2009-12-26
> **everettattebury said:**
> I filed a [_support request_]("http://support.scribd.com/requests/7838") with scribd, they're working on it.

It's still not working for me.. Did anyone find a solution for this?

---

### Post by arcane17 on 2010-05-11
:):) I solved the problem by using Google Chrome

kubuntu 10.04 (Lucyd Lynx)+ Current version google Chrome (5.0.375.29 beta)
 is working with Scribd !!

(But firefox does not)

(Precision : I tested with kubuntu (KDE), but this should work with ubuntu as well)

Thank you google! :):)

---

