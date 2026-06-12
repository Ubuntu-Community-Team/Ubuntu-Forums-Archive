---
title: "All downloaded files corrupted?"
date: 2005-12-16
forum: General Help
---

### Post by BlueNoteMKVI on 2005-12-16
I downloaded a big batch of files via Apollon (giFT), expecting at least a good portion of them to show up in my download directory.  Out of >50 files that successfully downloaded, 2 ended up in my download directory.

I was more than slightly annoyed at this.  I tried to find where they all went, and found the corrupted files directory.  This is packed FULL of files from months of attempting to download this way.  I tried to play some of them and found a few that were legitimately corrupt, but probably 95% of the files in there played just fine.

A bit of testing leads me to conclude that nearly every file downloaded via Gnutella is ending up in the corrupt directory.  Most things that come through openFT went into the downloaded directory, but it's rare that I find what I'm looking for on openFT - when I do, usually it downloads via Gnutella before the openFT file even begins.

So...what gives?  I searched for this a while back and I seem to remember seeing an article about routers causing problems with Gnutella.  I can't find that tonight.  Did I dream it?

Here's everything I can think of about my setup that could affect this:

Kubuntu 64 bit, upgraded to the latest stable packages (including universe and multiverse)
AMD XP ...3200 I think, 64 bit processor
1 gig of RAM
New hard drive..I don't remember the brand.  No problems with it.
Ethernet is on the motherboard.  This machine connects to my LinkSys wireless router, but it does so through a cable.  The wireless if for the laptop.  The wireless router connects to the LinkSys VOIP router, which connects to the DSL box and out into the world.

I can download files via Limewire on my other machine (cabled into the same router) that runs Windows XP.  This machine has XP installed in case I need it, but I haven't booted XP in weeks.  I don't think I have any P2P apps installed on it.  My laptop, which runs Kubuntu i386, is currently in the shop so I can't do any testing on that.

Thoughts?  Ideas?  Suggestions?

---

### Post by BlueNoteMKVI on 2005-12-18
I haven't received any responses to this question, and I've searched all over Google for some answers.  No luck yet.

Last night I installed Kubuntu for i386 onto a spare partition of my hard drive.  Same machine, same exact setup as far as hardware goes, but running in 32 bit mode.  My downloads work fine.  After installing a few missing programs I'm back in business.

I was fine when 64-bit meant I was going without some annoying flashy content on certain web pages.  When FireFox started crashing on me on a regular basis, I started to waver.  I fought with Amarok for a long time to get files to play right, a recent update to the Xine engine finally fixed that.  When I noticed that 99% of the files I downloaded ended up in the "corrupted" folder even though there was nothing (to my ears at least) wrong with them, I was ticked.

Thankfully I kept /home in a separate partition.  Most of my settings are already in place, and installing the apps I need is no problem thanks to the wonders of apt-get.  I'll probably reboot into the 64-bit partition every once in a while to do an apt-get upgrade, but until I see some significant upgrades happen there I won't be heading over there very often.  I've only been using this installation for a few hours now but I haven't noticed any significant difference in speed.

So if you're running 64-bit, kudos to you!  If you've got it working at 100% of what you need that's wonderful.  When it's as easy as "apt-get upgrade" to make things work, I'll go check it out again.  Until then I'm going to be quite happy in my 32 bit world.

---

