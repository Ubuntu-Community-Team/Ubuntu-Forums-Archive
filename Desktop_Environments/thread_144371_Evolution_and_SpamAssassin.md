---
title: "Evolution and SpamAssassin"
date: 2006-03-14
forum: Desktop Environments
---

### Post by nathanh on 2006-03-14
Have you been receiving lots of spam in evolution even though it used to be filtered? It's because spamassassin and evolution haven't been playing together in dapper. The problem is the introduction of the bogofilter eplug: it conflicts with the spamassassin eplug and stops them both from working. You can confirm this by starting evolution from the command line...

  (evolution:18521): e-utils-WARNING **: Plugin 'Spamassassin junk plugin'   failed to load hook 'org.gnome.evolution.mail.junk:1.0'

If you manually disable the bogofilter eplug then everything works again.

 $ cd /usr/lib/evolution/2.6/plugins
 $ mv org-gnome-bf-junk-plugin.eplug org-gnome-bf-junk-plugin.eplug.disabled 

You won't see that previous e-utils-WARNING the next time you start evolution, and spamassassin will work again.

---

### Post by pinguinus on 2006-04-05
More information here: 
[http://www.ubuntuforums.org/showthread.php?t=131782&highlight=spamassassin+evolution+bogofilter](http://www.ubuntuforums.org/showthread.php?t=131782&highlight=spamassassin+evolution+bogofilter)

---

