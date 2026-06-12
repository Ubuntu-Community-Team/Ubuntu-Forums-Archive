---
title: "two wiki pages"
date: 2008-04-08
forum: Desktop Environments
---

### Post by infinitezero on 2008-04-08
Is there a way to have to separate wikis (I am using Mediawiki)? I need one for employees and one for management.


Thanks,
iz

---

### Post by tamoneya on 2008-04-08
[http://www.mediawiki.org/wiki/Manual:Preventing_access](http://www.mediawiki.org/wiki/Manual:Preventing_access)
Just make one big wiki but make some pages restricted to just management.  Management will then have to login with a password.

---

### Post by infinitezero on 2008-04-08
Tamoneya,
I already require login to view or edit any of the pages (it is not a public wiki). Can I then lock it down even more?


Thanks,
iz

---

### Post by tamoneya on 2008-04-08
> Restrict viewing of certain specific pages

To prevent anyone but sysops from viewing a page, it can simply be deleted. To prevent even sysops from viewing it, it can be removed more permanently with the Oversight extension. To completely destroy the text of the page, it can be manually removed from the database. In any case, the page cannot be edited while in this state, and for most purposes no longer exists.

To have a page act normally for some users but be invisible to others, as is possible for instance in most forum software, is a very different matter. MediaWiki is designed for two basic access modes:

   1. Everyone can view every single page on the wiki (with the possible exception of a few special pages). This is the mode used by Wikipedia and its sister projects.
   2. Anonymous users can only view the Main Page and login page, and cannot edit any page. This is basically the same as the above, in terms of technical implementation (just an extra check for every page view), which is why it exists. This is the mode of operation used by certain private wikis such as those used by various Wikimedia committees.

If you intend to have different view permissions than that, MediaWiki is not designed for your usage. (See bug 1924.) Data is not necessarily clearly delineated by namespace, page name, or other criteria, and there are a lot of leaks you'll have to plug if you want to make it so (see security issues with authorization extensions for a sample). Other wiki software may be more suitable for your purpose. You have been warned. If you must use MediaWiki, there are two basic possibilities:

   1. Set up separate wikis with a shared user database, configure one as viewable and one as unviewable (see above), and make interwiki links between them.
   2. Install a third-party hack or extension. You will have to reapply it every time you upgrade the software, and it may not be updated immediately when new security fixes or upgrades of MediaWiki are released. Third-party hacks are, of course, not supported by MediaWiki developers, and if you're having problems you shouldn't ask on MediaWiki-l, #mediawiki, or other official support channels. One hack for this is the hidden namespaces patch; a number of others are listed in Category:Page specific user rights extensions. Read about security issues with authorization extensions if you plan to use one of those.


This is from the page i just linked. If you havent gotten too far on your project I would recommend using different wiki software as they recommend.  Otherwise I like their first idea.  Use two different wikis one for management and one for employees.

---

### Post by infinitezero on 2008-04-08
Tamoneya,
Thanks I will take a closer look at that link.


iz

---

