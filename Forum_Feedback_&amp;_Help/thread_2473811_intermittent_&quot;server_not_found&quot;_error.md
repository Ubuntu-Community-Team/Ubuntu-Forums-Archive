---
title: "intermittent &quot;server not found&quot; error"
date: 2022-04-14
forum: Forum Feedback &amp; Help
---

### Post by &amp;KyT$0P# on 2022-04-14
Is anyone else getting intermittent "server not found" errors when browsing this forum?

Firefox 99.0.1 here -
> Hmm. We’re having trouble finding that site.

We can’t connect to the server at ubuntuforums.org.

Not seeing such problems browsing any other site.

---

### Post by Bashing-om on 2022-04-14
Hey halogen2 -

Negative - No issues when on the forum last night and none in a fresh login now.

My browser however is slimjet.

[INDENT]hope this helps-
[/INDENT]

---

### Post by TheFu on 2022-04-14
No, but most interactions today have been extremely delayed.  Normal is 2 sec between queries/posts. Today it has been more like 30 seconds for me.
When it first happened this morning, I checked some other internet servers and websites and with my ISP for bandwidth issues. All were fine. Just these forums showing unexpected issues.

---

### Post by &amp;KyT$0P# on 2022-04-16
Thanks both for the replies.  So far I haven't seen this server not found error again since that day.  Still seeing some delays like TheFu mentioned, but they're not as bad as they were when this error was happening.  Will test using a Chromium based browser in the event this happens again.

---

### Post by &amp;KyT$0P# on 2022-04-20
I have not seen this error since.  Either it just cleared up on its own, or it went away because I un-checked "Uncloak canonical names" in uBlock Origin.  Not sure which.

However I do still see intermittent delays on this forum in Firefox, so tried using ungoogled-chromium for this site today.  No errors and zero significant delays.

I don't currently have time to troubleshoot what in my Firefox is causing ubuntuforums-specific intermittent delays, so will just continue using ungoogled-chromium for this forum for now unless someone else affected finds the culprit.  Thanks again Bashing-om for the Slimjet hint.

---

### Post by Bashing-om on 2022-04-20
halogen2 :D

slimjet: thus far I can find no gripe using it - just a very small nuisance to upgrade.

But in all honesty - I never was a big fan of FireFox, though I have and do sometimes use FireFox.

[INDENT]if the tool fits
[INDENT][INDENT][INDENT]use IT[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2022-04-20
> **halogen2 said:**
> Is anyone else getting intermittent "server not found" errors when browsing this forum?

Firefox 99.0.1 here -


Not seeing such problems browsing any other site.

Same here, just noticed this thread.
this helped a bit>> "**about;config**" changed "**network.dns.disableIPv6**" to** true**.
so far today no real issues.

---

### Post by &amp;KyT$0P# on 2022-04-20
> **1fallen said:**
> this helped a bit>> "**about;config**" changed "**network.dns.disableIPv6**" to** true**.

Nice find 1fallen!  Thanks, I'll test it out.

---

### Post by #&amp;thj^% on 2022-04-20
> **halogen2 said:**
> Nice find 1fallen!  Thanks, I'll test it out.

Fingers Crossed, at times I find with firefox I'll have to clear my history >>Clear Recent History.
too many tabs opened logged in other sites. (might try that as well) I do right click and save the history to a drive though.

---

### Post by &amp;KyT$0P# on 2022-04-21
Unfortunately the pref change was not the solution for me, I'm still seeing the delays with Firefox.

---

### Post by #&amp;thj^% on 2022-04-23
same for me today, editing this: [https://ubuntuforums.org/showthread.php?t=2474160&p=14091833#top](https://ubuntuforums.org/showthread.php?t=2474160&p=14091833#top)
tells me forbiden
hope it gets fixed soon very tiresome

---

### Post by &amp;KyT$0P# on 2022-04-23
> **halogen2 said:**
> tried using ungoogled-chromium for this site today.  No errors and zero significant delays.

Spoke too soon.  The delays are still there with ungoogled-chromium.  It's just much less frequent than when using Firefox.

---

### Post by Bashing-om on 2022-04-23
As a thought - try the FF .deb ?
[https://balintreczey.hu/blog/firefox-on-ubuntu-22-04-from-deb-not-from-snap/](https://balintreczey.hu/blog/firefox-on-ubuntu-22-04-from-deb-not-from-snap/)

- a be a yes ?-

---

### Post by &amp;KyT$0P# on 2022-04-23
I don't use snap at all.  Firefox is installed from tarball, ungoogled-chromium is installed as a flatpak.  I don't see how using Firefox as a deb would be any different?

---

