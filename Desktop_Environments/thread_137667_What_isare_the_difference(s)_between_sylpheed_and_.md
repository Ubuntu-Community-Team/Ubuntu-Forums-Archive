---
title: "What is/are the difference(s) between sylpheed and sylpheed-claws?"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Rumor on 2006-02-28
Well, I guess the topic is the subject. I am using sylpheed at the moment as my mail client. I know sylpheed-claws is a fork off it, but what are the differences between the two?

---

### Post by kaamos on 2006-02-28
I think claws has more features like ssl authentication and a lot of plugins.
> sylpheed-claws-ghostscript-viewer - PostScript/PDF viewer plugin for the Sylpheed Claws mail client
sylpheed-claws-maildir-plugin - Maildir++ support plugin for the Sylpheed Claws mail client
sylpheed-claws-pgpinline-plugin - PGP-inline checking/decryption plugin for Sylpheed Claws
sylpheed-claws-clamav - Clam AntiVirus plugin for Sylpheed Claws
sylpheed-claws-dillo-viewer - HTML viewer plugin for Sylpheed Claws using Dillo
sylpheed-claws-gtk2-clamav - Clam AntiVirus plugin for the Sylpheed Claws GTK2 mail client
sylpheed-claws-gtk2-dillo-viewer - HTML viewer plugin for Sylpheed Claws GTK2 using Dillo
sylpheed-claws-gtk2-pgpinline - PGP/inline plugin for Sylpheed Claws GTK2
sylpheed-claws-gtk2-pgpmime - PGP/MIME plugin for Sylpheed Claws GTK2
sylpheed-claws-gtk2-plugins - Installs plugins for the Sylpheed Claws GTK2 mail client
sylpheed-claws-gtk2-spamassassin - SpamAssassin plugin for Sylpheed Claws GTK2
sylpheed-claws-gtk2-trayicon - Notification area plugin for Sylpheed Claws GTK2
sylpheed-claws-image-viewer - Image viewer plugin for Sylpheed Claws
sylpheed-claws-pgpmime - PGP/MIME plugin for Sylpheed Claws
sylpheed-claws-plugins - Various plugins for the Sylpheed Claws mail client
sylpheed-claws-spamassassin - SpamAssassin plugin for Sylpheed Claws
sylpheed-claws-trayicon - Notification area plugin for Sylpheed Claws


---

### Post by colinleroy on 2006-03-21
Sylpheed-Claws and Sylpheed have many differences.
As stated on S-C's homepage:
[INDENT]Sylpheed-Claws started as the bleeding-edge version of Sylpheed, in order to act as a testbed for new features for Sylpheed. The idea was to regularly resync with Hiroyuki's main branch, and vice-versa. Sylpheed-Claws then evolved into the stable extended version of Sylpheed, and is now an entity in its own right, mainly due to different goals and the fact that syncing both codebases doesn't happen anymore.[/INDENT]

You can see a list of features that are only available in Claws (a bit messy, sorry) at [http://claws.sylpheed.org/features.php](http://claws.sylpheed.org/features.php) . 

The most important difference in my opinion is Claws' support of plugins, which allow us to have really nice addons, like RSSyl (an rss aggregator), vCalendar (for people who need to interact with Outlook-using managers ;-)) and more. You can see the complete current list of plugins at 
[http://claws.sylpheed.org/manual/sylpheed-claws-manual.html#ch_plugins](http://claws.sylpheed.org/manual/sylpheed-claws-manual.html#ch_plugins) and [http://claws.sylpheed.org/plugins.php](http://claws.sylpheed.org/plugins.php)

To be short, Sylpheed-Claws rocks more ;-). (ok, I'm biased, I'm one S-Claws authors).

We also have an up-to-date Breezy repository, if you want to try the latest version, follow the instructions at [http://claws.sylpheed.org/downloads.php](http://claws.sylpheed.org/downloads.php) (Ubuntu section). A Dapper repository will come soon.

---

