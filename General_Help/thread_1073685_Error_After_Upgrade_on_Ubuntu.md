---
title: "Error After Upgrade on Ubuntu"
date: 2009-02-18
forum: General Help
---

### Post by Cerin on 2009-02-18
Hi,

I'm running Mediawiki 1.11.2 on Ubuntu 8, and after a recent update, I'm now getting the error:
[I]
Warning: Missing argument 5 for MediaWiki::initialize(), called in /usr/share/mediawiki/index.php on line 89 and defined in /var/lib/mediawiki/includes/Wiki.php on line 52

Fatal error: Call to a member function getCheck() on a non-object in /var/lib/mediawiki/includes/Wiki.php on line 137[/I]

Why would an update break Mediawiki's homepage, and how can I fix it?

Interestingly, Google returns lot's of sites with this error, but they're all Mediawiki sites containing the error, and not anyone discussing why the error occurs or how to fix it.

Regards,
Chris

---

