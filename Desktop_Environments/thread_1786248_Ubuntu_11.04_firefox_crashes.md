---
title: "Ubuntu 11.04 firefox crashes"
date: 2011-06-19
forum: Desktop Environments
---

### Post by haoniukun on 2011-06-19
Hi all,
The problem trapped me for about one month.
After upgrading Ubuntu from 10.10 to 11.04, my firefox regularly crashes.
Today I started firefox from the console, and I got the following error:
(firefox-bin:2579): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
I don't know if this problem arose from dbus.
Can anyone here help me resolve the problem?

Thanks for any hints in advance.

---

### Post by lovinglinux on 2011-06-20
Disable Global Menu Bar Integration in the Firefox Add-ons Manager. To open it, type **about:addons** in the address bar.

---

### Post by haoniukun on 2011-07-08
> **lovinglinux said:**
> Disable Global Menu Bar Integration in the Firefox Add-ons Manager. To open it, type **about:addons** in the address bar.
 Hi lovinglinux,
Really appreciate your reply. I tried your method. But it doesn't solve the problem. I don't know if it has something to do with flash on  the page. If the web page contains flash, chrome doesn't show the web page at all. Firefox can show the web page, but it randomly crashes. It makes me really headache.:(

---

### Post by lovinglinux on 2011-07-08
> **haoniukun said:**
> Hi lovinglinux,
Really appreciate your reply. I tried your method. But it doesn't solve the problem. I don't know if it has something to do with flash on  the page. If the web page contains flash, chrome doesn't show the web page at all. Firefox can show the web page, but it randomly crashes. It makes me really headache.:(

Try [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/").

---

### Post by a&amp;a on 2011-07-14
Exactly the same problem on my machine. I recently installed SRWare Iron browser, because in Firefox even regular things, without Flash (such as purely html/js website or rss feed) make it hanging.

---

### Post by lovinglinux on 2011-07-14
> **a&a said:**
> Exactly the same problem on my machine. I recently installed SRWare Iron browser, because in Firefox even regular things, without Flash (such as purely html/js website or rss feed) make it hanging.

See my [tutorials]("http://www.webgapps.org/tutorials/firefox") on troubleshooting and optimization.

---

### Post by haoniukun on 2011-07-27
> **a&a said:**
> Exactly the same problem on my machine. I recently installed SRWare Iron browser, because in Firefox even regular things, without Flash (such as purely html/js website or rss feed) make it hanging.
 Yes. I have the same problem. And my other program also random crashes, especially thunderbird. This made me really regret to upgrade to Natty. It truly destroyed my work machine. Maybe I need to reinstall it some time later.

---

### Post by haoniukun on 2011-07-27
> **lovinglinux said:**
> See my [tutorials]("http://www.webgapps.org/tutorials/firefox") on troubleshooting and optimization.
Hi. Really appreciate your time for reply.
In fact not only FF, but also other programs randomly crashes.
I don't know if it has something to do the the rendering engine.
The problem is extremely serious if the web page contains flash.
Chrome even doesn't show the web page.

---

### Post by M1ttenz11 on 2011-08-03
there is something you can get for chromium called flash block, stops videos loading up straight away.  you have to click on a video to allow it load up, then you have to click to play.
this will also block annoying ads on the side about washing and stuff.

my girlfriend had the exact same problem when she used natty, so she dropped to 10.04 and doesn't have a problem, but she used the flash block, and found that less videos crashed, and if the did, they were easier refreshed.
Good luck.

---

### Post by lovinglinux on 2011-08-03
> **haoniukun said:**
> Hi. Really appreciate your time for reply.
In fact not only FF, but also other programs randomly crashes.
I don't know if it has something to do the the rendering engine.
The problem is extremely serious if the web page contains flash.
Chrome even doesn't show the web page.

Could be a video driver issue or even bad memory.

---

### Post by haoniukun on 2011-08-08
Interesting advice. I'll have a try.
Thank you for your reply.
In fact, I also face the same problem after upgrade.
How does your girlfriend change back to 10.04?
Reinstall the system again?
I'm also thinking of downgrade my system.
 
> **M1ttenz11 said:**
> there is something you can get for chromium called flash block, stops videos loading up straight away. you have to click on a video to allow it load up, then you have to click to play.
this will also block annoying ads on the side about washing and stuff.
 
my girlfriend had the exact same problem when she used natty, so she dropped to 10.04 and doesn't have a problem, but she used the flash block, and found that less videos crashed, and if the did, they were easier refreshed.
Good luck.

---

### Post by haoniukun on 2011-08-08
> **lovinglinux said:**
> Could be a video driver issue or even bad memory.
Hi lovinglinux,
Really appreciate your keeping an eye on my problem.
My memory works fine on Windows platform.
So I prefer a video driver issue.
In fact, my laptop often hangs when shutting down.
The problem arises after system upgrade from 10.10 to 11.04.
I'm using Dell 13R with ATI video card.
Do you think I should reinstall my driver?

---

### Post by lovinglinux on 2011-08-08
> **haoniukun said:**
> Hi lovinglinux,
Really appreciate your keeping an eye on my problem.
My memory works fine on Windows platform.
So I prefer a video driver issue.
In fact, my laptop often hangs when shutting down.
The problem arises after system upgrade from 10.10 to 11.04.
I'm using Dell 13R with ATI video card.
Do you think I should reinstall my driver?

I don't know much about drivers, but it could be an ATI issue. Try to boot from a Live CD and check if the problem persists.

---

