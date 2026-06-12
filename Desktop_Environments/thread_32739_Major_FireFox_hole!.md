---
title: "Major FireFox hole!"
date: 2005-05-09
forum: Desktop Environments
---

### Post by nocturn on 2005-05-09
[http://www.theregister.co.uk/2005/05/09/firefox_0day_exploit/](http://www.theregister.co.uk/2005/05/09/firefox_0day_exploit/)

It seems that FF is vulnerable to a combination of 2 exploits.  
It allows a site to run code in the context of the user running FF.

1.0.3 is also vulnerable.   And I thought we would be safe when the patches from 1.0.3 hit the Ubuntu version.

---

### Post by XDevHald on 2005-05-09
[QUOTE=nocturn][http://www.theregister.co.uk/2005/05/09/firefox_0day_exploit/](http://www.theregister.co.uk/2005/05/09/firefox_0day_exploit/)

It seems that FF is vulnerable to a combination of 2 exploits.  
It allows a site to run code in the context of the user running FF.

1.0.3 is also vulnerable.   And I thought we would be safe when the patches from 1.0.3 hit the Ubuntu version.[/QUOTE]
 Great to hear this, now I can re-dev my files to somehow fix this.

Thanks for the updates, greatly appreciated!

---

### Post by shakin on 2005-05-09
The attack relies on tricking the browser into executing code from one site, but doing it with the priviledges of a whitelisted site that's allowed to install software. The Mozilla folks have made changes to the mozilla.org sites so that this attack won't work with the default whitelisted sites. In order for the attack to successfully work the attacker would have to guess at which site is in your whitelist.

It's probably best to remove obvious sites like extension mirror, but for the most part this attack has been mitigated until a browser patch can be completed.

---

### Post by jodef on 2005-05-09
> It's probably best to remove obvious sites like extension mirror, but for the most part this attack has been mitigated until a browser patch can be completed. Thanks for the heads up removed all sites until a patch released.

---

### Post by nocturn on 2005-05-09
Is it just me, or is FireFox starting to feel like swiss cheese?

---

### Post by nocturn on 2005-05-09
Amost forgot, I have filled a bugreport here:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=10562](https://bugzilla.ubuntu.com/show_bug.cgi?id=10562)

---

### Post by jodef on 2005-05-09
The workaround for now according to release is > Users are advised to disable JavaScript and the software installation option within Firefox pending a more comprehensive fix from the Mozilla Foundation. > Is it just me, or is FireFox starting to feel like swiss cheese?No software is 100% secure despite claims made to the contrary.

---

### Post by jodef on 2005-05-09
**Update** 
[Mozilla Talkback](http://www.mozillazine.org/talkback.html?article=6582) provides details of the vulnerability which was apparently leaked by someone. The fix > he Secunia advisory suggests disabling JavaScript as a workaround; however, simply disabling software installation (Web Features panel of the Options/Preferences window in Firefox 1.0.3 or the Content panel in the latest trunk builds) eliminates the problem. We understand that a change made to Mozilla Update has made the vulnerability effectively unexploitable if you only have update.mozilla.org and addons.mozilla.org in your software installation whitelist (accessible from the Web Features or Content panel in the Options/Preferences window), which is the default setting.

---

### Post by nocturn on 2005-05-09
[QUOTE=jodef] No software is 100% secure despite claims made to the contrary.[/QUOTE]

That's true, but there have been a great number of vuln in FF lately.  .1, .2 and .3 followed rather quickly, .4 shouldn't be far behind.

---

### Post by cutOff on 2005-05-09
hmm... does anybody know about this bug??

[https://bugzilla.mozilla.org/show_bug.cgi?id=131456](https://bugzilla.mozilla.org/show_bug.cgi?id=131456)

---

### Post by fng on 2005-05-09
[QUOTE=nocturn]Is it just me, or is FireFox starting to feel like swiss cheese?[/QUOTE]

More people use it, so more bugs are found.
More people use it, so its becoming more and more attractive for bad people to find holes in it.  
...

---

### Post by YourSurrogateGod on 2005-05-09
How can I update everything that I need for FireFox?

---

### Post by bonifacio on 2005-05-09
Is the patch going to be on the regular repo or backports?

---

### Post by nocturn on 2005-05-10
[QUOTE=fng]More people use it, so more bugs are found.
More people use it, so its becoming more and more attractive for bad people to find holes in it.  
...[/QUOTE]

That has always been the defense of M$, so not really an excuse for FF to go the same way.  
To beat them, we need our security not te be equal, but to be better (which is the reason for the enormous rise of FF).

The fact that there are bugs is not the main issue, the problem is that they offer access to code execution or file alteration is.  Maybe there needs to be some generic safeguard limiting the impact of such bugs, much like the PaX patches for the kernel...

---

### Post by nocturn on 2005-05-10
[QUOTE=bonifacio]Is the patch going to be on the regular repo or backports?[/QUOTE]

The fixes are coming via the standard Hoary repositories, although it might take a while (1.0.3 fixes are still pending).
The quickest way to have a patched version is backports, Jdong is very good at responding to security issues.

---

### Post by jcooper on 2005-05-10
[QUOTE=nocturn]
To beat them, we need our security not te be equal, but to be better (which is the reason for the enormous rise of FF).

The fact that there are bugs is not the main issue, the problem is that they offer access to code execution or file alteration is.  Maybe there needs to be some generic safeguard limiting the impact of such bugs, much like the PaX patches for the kernel...[/QUOTE]


All software will have vulnerabilities and bugs. The key issue here is the lead time between disclosure/exploit code and the fix. Open source has always been great and minimising this lead time. Microsoft, on the other hand, takes months to fix things. I am not concerned by this issue, as I know full well that it will be fixed in no time, and the temporary workaround is a minor change (i.e. not disabling scripting etc).

---

### Post by nocturn on 2005-05-13
[QUOTE=jcooper]All software will have vulnerabilities and bugs. The key issue here is the lead time between disclosure/exploit code and the fix. Open source has always been great and minimising this lead time. Microsoft, on the other hand, takes months to fix things. I am not concerned by this issue, as I know full well that it will be fixed in no time, and the temporary workaround is a minor change (i.e. not disabling scripting etc).[/QUOTE]

The window of oportunity/exposure is indeed a critical factor for security bugs.  But regardless, applications would do well to fail-closed instead of failing open.  Meaning that an application crash is preferable to being compromised.
That's where Pax for the kernel comes in well.

Since FF is one of the most common and most exposed pieces of software you have (when running a desktop system),  it would improve your overall security greatly if it had some sort of generic mechanism to catch exploits...

That said, kudos the the FF development team for releasing the update so quickly.

I do hope response times for Ubuntu to FF fixes improve in the future (Hoary took almost a month to get 1.0.3 fixes, Warty is still vulnerable).

---

### Post by Segovia on 2005-05-13
[QUOTE=nocturn]I do hope response times for Ubuntu to FF fixes improve in the future (Hoary took almost a month to get 1.0.3 fixes, Warty is still vulnerable).[/QUOTE]
Yep.  I'm a little concerned about that too.  I'm curious as to why the Firefox stuff is taking so long to hit Ubuntu?  They have been very fast in getting fixes up for other stuff.

---

### Post by nocturn on 2005-05-13
[QUOTE=Segovia]Yep.  I'm a little concerned about that too.  I'm curious as to why the Firefox stuff is taking so long to hit Ubuntu?  They have been very fast in getting fixes up for other stuff.[/QUOTE]

Part of the reason is that they take fixes from 1.0.3 and apply them to 1.0.2.  After that, there is a series of QA tests.

But I am really concerned about Warty, it is included in several USN's, but no updates for FF whatsoever (not from .2 or .3).

---

### Post by DutchLau on 2005-05-13
Does this also affect Linux? As far as I know, the coders probably won't bother on writing programs for Linux, even though it is Java-script.

---

