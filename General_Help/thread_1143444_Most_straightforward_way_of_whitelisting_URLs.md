---
title: "Most straightforward way of whitelisting URLs"
date: 2009-04-29
forum: General Help
---

### Post by lykwydchykyn on 2009-04-29
Here's the situation:  I'm creating a web kiosk for work.  When I've done this in the past, it's usually just for one page or site (usually hosted locally), so I can lock it down easily with iptables.

This time, I've got a laundry list of sites that need to be accessed from this kiosk, and it may potentially grow. It gets pretty tedious after a while to create iptables rules for all the possible IP addresses that might need to be accessed, and then of course someone might change ISP's and I'll be always maintaining this thing.

So what I need is the most straightforward, basic way of giving Linux a list of URLs (not IP addresses) which can be accessed through the browser, and blocking everything else.

I played with squid for half a day and didn't quite get it figured out; I kept finding conflicting tutorials on how to write rules, and it's not entirely clear to me if I even got the browser routed through it.

I have set up dansguardian before, but I don't need content filtering or all the extra stuff that goes with it, so it seems overkill.

I installed squidguard, but couldn't see how it helped me much.

Anyone have a good recommendation?  I don't care if it's GUI or CLI, I don't even have gnome installed on this thing.

---

### Post by mb_webguy on 2009-04-29
Well, you could try the ProCon Latte extension in Firefox.  It will whitelist URLs *only* for the browser, and not other network clients, but it's fairly easy to manage.  And if you're making a web kiosk, you don't really need to have other network clients (e.g. FTP, IM, torrent) installed anyway.  It's also a helpful extension for a kiosk because it allows you to lock down certain menu items with a password, so even if someone knows how to drop out of kiosk mode, they can't do much.

---

### Post by lykwydchykyn on 2009-04-30
I think that's gonna be the answer.  Thanks, it works great!

---

### Post by i.r.id10t on 2009-04-30
I do mine by locking down firefox with the rkiosk extension, and setting the proxy for firefox to be a squid instance running on localhost.  And then squid blocks *all* domains, then allows the ones we want (*.edu, .google.com for search results, .cc.fl.us for old college domains, etc)

---

