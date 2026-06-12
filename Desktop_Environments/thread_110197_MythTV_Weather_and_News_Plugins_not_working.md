---
title: "MythTV Weather and News Plugins not working"
date: 2005-12-30
forum: Desktop Environments
---

### Post by new2hoary on 2005-12-30
I've got MythTV installed and the TV part is working fine.

I installed the weather and news plugins, but can't get them to work.

The weather plugin just times out, and the news plugin reports 'failed to retrieve news'.

I have shorewall, dansguardian, and squid installed. I've used shorewall to make squid act as a transparen proxy so that it can't be bypassed.
If I log in with the account MythTV runs under, I can paste one of the urls the news plugin uses into firefox and the news feed appears. This would suggest there is no problem with permissions with the shorewall/proxy setup.

If I look at the squid logs I can see the request being made when I use firefox to access a news feed. If I use MythTV, it fails, and I don't see anything in the squid log.

This one has got me stumped - anyone got any ideas? Anyone got these plugins working?

The MythTV version is the one from Breezy version 0.18.1-3. The plugins are also from Breezy, and are also 0.18.1-3.

TIA

---

