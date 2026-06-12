---
title: "How can I enable ext4?"
date: 2009-03-31
forum: General Help
---

### Post by Mulenmar on 2009-03-31
When I went to install Arch Linux, I noticed a filesystem option I'd never heard of: ext4.

I've done some research, and it seems to be faster than ext3. I noticed it's not enabled in Ubuntu, so I have some questions.

1. How do I enable ext4? I think kernel modification is needed, but I'd need a walkthrough on that.

2. If anyone reading this has used ext4 recently, how stable was it and what types of usage did you notice had better performance with ext4 vs ext2/3, reiserfs?

---

### Post by kanikilu on 2009-03-31
Apparently Ext4 will be an option in Jaunty. I haven't tried out the beta yet, though, so don't really have a personal opinion on it...

According to this page, it doesn't look too promising if you intend to try to upgrade from Ext3, while preserving your data:

[http://www.automaticable.com/2009-03-12/testing-ubuntu-jaunty-and-ext4-without-trashing-your-data/](http://www.automaticable.com/2009-03-12/testing-ubuntu-jaunty-and-ext4-without-trashing-your-data/)

If it's a new install and not an upgrade, it's probably fine...

---

### Post by fcuk112 on 2009-03-31
ext4 is available in the next version of Ubuntu - Jaunty Jackelope.  only a few weeks to go before it's released!

---

### Post by Mulenmar on 2009-03-31
Dang, I have to wait a few weeks?

I was hoping to try out the performance increase while keeping with an otherwise known-stable version of Ubuntu. That way, I don't have to redownload EVERYTHING in a Jaunty version.

---

### Post by steeleyuk on 2009-03-31
There have been reports of data loss with ext4. Use with caution.

---

### Post by arepaking on 2009-04-02
> **steeleyuk said:**
> There have been reports of data loss with ext4. Use with caution.

Could you provide some additional information about this data losses? any web site to read?

---

### Post by leonardo_neo on 2009-04-02
> **arepaking said:**
> Could you provide some additional information about this data losses? any web site to read?

[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892]("http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892")

I got this from forum itself. Hope this answers your question :)

---

### Post by HermanAB on 2009-04-02
Ext3 is a good upgrade to an existing Ext2, but the jury is still out on Ext4.  i sure won't use it any time soon, if ever.

JFS and XFS are more mature, more efficient, faster and better designed.  So you are probably better off with one of those.

---

