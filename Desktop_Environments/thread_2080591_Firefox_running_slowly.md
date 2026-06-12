---
title: "Firefox running slowly"
date: 2012-11-04
forum: Desktop Environments
---

### Post by welshmike on 2012-11-04
I'm running Firefox 16.0.2 on Ubuntu 10.04.
It is now running slowly in opening some web pages, the window frequently goes dim and I have noticed from my ADSL modem that there is no traffic until the window goes bright again.
Could this be something to do with Mesa? If so is there a fix/bypass please?
I note that I do not get any problems with the Chromium browser 22.0.1229.79.

---

### Post by Abhinav Kumar on 2012-11-04
> **welshmike said:**
> I'm running Firefox 16.0.2 on Ubuntu 10.04.
It is now running slowly in opening some web pages, the window frequently goes dim and I have noticed from my ADSL modem that there is no traffic until the window goes bright again.
Could this be something to do with Mesa? If so is there a fix/bypass please?
I note that I do not get any problems with the Chromium browser 22.0.1229.79.
Hi
Try increasing maxrequest in http pipelining in firefox.
Type **about:config** as url.
Confirm OK
Search for pipelining
Increase the number of **network.pipelining.http.maxrequests** from your present value.
Restart firefox

Also try to use only those extensions which are needed. otherwise disable or un-install them.

Regards,
Abhinav

---

### Post by welshmike on 2012-11-04
> **Abhinav Kumar said:**
> Hi
Try increasing maxrequest in http pipelining in firefox.
Type **about:config** as url.
Confirm OK
Search for pipelining
Increase the number of **network.pipelining.http.maxrequests** from your present value.
Restart firefox

Also try to use only those extensions which are needed. otherwise disable or un-install them.

Regards,
Abhinav

Thanks. Here's what I found that may be relevant

network.http.pipelining;false
(edit) have since changed above to network.http.pipelining;true
to see how it goes.
network.http.pipelining.max-optimistic-requests;4
network.http.pipelining.maxrequests;32

any suggestions please?

---

### Post by mardybear on 2012-11-04
Hi welshmike...

In my experience pipelining may/may not improve browser performance depending on your computer hardware and internet service provider. You'll need to tinker and test to find your optimal settings.

As already mentioned, uninstall all unnecessary add-ons.

If you're prepared to learn/use NoScript (also blocks flash), flashblock and/or adblock are add-ons that can really reduce your CPU usage when browsing.

Here are some of my favourite about:config changes to help my firefox run leaner, adjust to your liking, restart to ensure changes are in effect:
browser.bookmarks.max_backups, 3
browser.cache.offline.enable, false
browser.chrome.favicons, false)
browser.chrome.image_icons.max_size, 0
browser.chrome.site_icons, false
browser.display.show_image_placeholders, false
browser.offline, false
browser.sessionhistory.max_entries, 5
browser.sessionhistory.max_total_viewers, 5
browser.sessionstore.interval, 45000
browser.sessionstore.max_tabs_undo, 3
browser.sessionstore.max_windows_undo, 1
browser.tabs.animate, false
dom.ipc.plugins.enabled, false
ui.submenuDelay, 1

My dualboot Ubuntu runs firefox slower than my windowsXP. Although it may seem counter-intuitive, try changing your about:config network.http.max-connections from 256 down to 30 or 60. Restart and see if any better.

If all else fails, create a new firefox profile (resets everything) to see if this gets things running fresh again.

mardybear

---

### Post by black veils on 2012-11-05
try disabling the add-on** ubuntu firefox modifications**. if i ever get slow performance, thats what helps me.

---

### Post by welshmike on 2012-11-05
Hi mardybear,

Well my Firefox is running fast again now. It may well have been my ISP TalkTalk throttling broadband rate as it was over the weekend. Strangely I also noticed that the light on my modem/router stayed on and did not flash when I browsed to a different webpage from what I was looking at. 

Cheers
Mike

---

### Post by welshmike on 2012-11-05
> **black veils said:**
> try disabling the add-on** ubuntu firefox modifications**. if i ever get slow performance, thats what helps me.

I spoke too soon and even with the mods disabled FF has gone into dull window and slow down just now. Time to use Chromium instead perhaps.

---

### Post by mardybear on 2012-11-05
Hi welshmike.

Sorry to hear your performance improvement was intermittent. My experience is that Chromium uses a lot more resources than Firefox plus i have more trust in Mozilla than Google. I would never personally change to Chromium.

You never mentioned if you tried all the changes and experimented. Did you try the about:config changes? Did you disable any add-ons (some are known to cause performance issues)? Did you restart Firefox between tweak attempts? Did you create/try a new profile? Do you regularly clear your cache (generally a good thing)?

Couple other things to try in your Firefox settings:

Encryption: open firefox preferences, click on advanced, select the encryption tab and under certificates, mark 'select one automatically'.

Network settings: open firefox preferences, click on advanced, select the network tab and open settings, if you don't use a proxy (most don't) then mark 'no proxy'.

mardybear

---

### Post by welshmike on 2012-11-06
Hi mardybear,

I applied all the changes you suggested and there was no improvement.
In fact this morning Firefox crashed.
[IMG]http://www.hantsnwa.org.uk/Screenshot.png[/IMG]

---

### Post by mardybear on 2012-11-06
Hi welshmike...

Sorry i wasn't much help.

mardybear

---

### Post by welshmike on 2012-11-06
Hi mardybear,

You have helped thanks with the following in one of your earlier posts.

"If all else fails, create a new firefox profile (resets everything) to see if this gets things running fresh again."

I did just that and firefox is now working well thus far. 

Mike

---

### Post by mardybear on 2012-11-06
> **welshmike said:**
> I did just that and firefox is now working well thus far.Mike
Howdy Mike.

If you're so inclined you can always trial the previously recommended tweaks on your fresh profile, especially since they are easily reversible. As a Firefox fanboy, it's really good to hear it's running better for you.

Take care,

mardybear

---

### Post by welshmike on 2012-11-12
Firefox no better on 10.04 (due to it possibly having software updates so that is essentially the same version as on 12.04).

"Mozilla Firefox

"In 2012, Mozilla Firefox was mired with various critical bugs over iterative releases that caused the software to act sluggish."

[2012 in Review: Tech Turkeys of the Year by Jason Perlow]("http://www.zdnet.com/2012-in-review-tech-turkeys-of-the-year-7000007207/")

---

### Post by ohagangt on 2012-11-19
Hi,
am running 12.04 and had the same problem. The fix for me was to goto add-ons and disable "Global Menu-Bar integration".

Gary

---

### Post by welshmike on 2012-11-19
I don't have "Global Menu-Bar integration" add-on and it does not appear in the list.
However my Firefox has been behaving OK recently.

---

